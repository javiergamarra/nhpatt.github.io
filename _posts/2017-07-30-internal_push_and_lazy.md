---
title: Internal, push and lazy
date: 2017-07-30T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/internal_push_and_lazy
permalink: /internal_push_and_lazy/
image: internal_push_and_lazy.png
categories:
  - rx
  - reactive
  - development
---

Talking about Rx ([RxJava](https://github.com/ReactiveX/RxJava) or [RxJS](https://github.com/ReactiveX/rxjs)) I usually 
mention that streams use *internal* iteration (vs *external*), *push* * based (vs *pull*) and are *lazy* (vs *eager*).

But it's a theoretical distinction that is **hard to grasp**. I'm going to try to explain it here.

Let's start with *external* vs *internal* iteration.

## Internal vs external iteration

When we use a *for each* or an iterator we are, **explicitly**, managing the iteration. 
We have to write a loop and code when to advance to the next element. When we write:

```javascript
// You can ignore the array declaration and focus in for...
// Creating an array from 0 to 9
const arr = Array.from({length: 10}, (_, i) => i); 

for (let i = 0; i < 10; i++) {
    console.log(arr[i]); // 0, 1, 2, 3...
}
```

We are the ones responsible for managing the control flow (with the *i<10* and *i++* code) and we lose the opportunity 
of having automatic improvements in performance, reordering, parallelism or laziness. 
**If we want those features we have to implement them ourselves**.

In those lines, we can see two things:

* Code for iterating (for, arr[i]...)
* Code for operating with the values (console.log)

The responsibilities of those lines are different but the code is mixed, the act of iterating can't be separated 
with the act of processing the result. 

That code also has these drawbacks:

* It is inherently sequential (it's ordered by the *i < 10; i++*)
* It leads to imperative code
* It is difficult to parallelize

### Internal iteration

Internal iteration is different, and follows the Hollywood principle, "Don’t Call Me, I’ll Call You". In internal iteration we don't 
have to worry about coding when to loop, we just say **"perform this operation on the elements of the collection"**.

```javascript
// You can ignore the array declaration and focus in the map
const arr = Array.from({length: 10}, (_, i) => i);

arr.map(x => console.log(x));
```

Let's see a classical java example to see all the differences. 
In this example, we are filtering a list of scores to get only those who have more than a 4. Easy enough. 

```java
List<Integer> scores = Arrays.asList(4, 2, 3, 1, 6, 8, 2, 10);

List<Integer> passed = getPassed(scores);
System.out.println("Passed: " + passed);

private static List<Integer> getPassed(List<Integer> scores) {
    List<Integer> passed = new ArrayList<>();
    for (Integer score : scores) {
        if (score > 4) {
            passed.add(score);
        }
    }
    return passed;
}
```

Let's add another condition to get the worst and the best (1 & 10) scores. Unfortunately, we need another method:

```java
private static List<Integer> getExtreme(List<Integer> scores) {
    List<Integer> list = new ArrayList<>();
    for (Integer score : scores) {
        if (score == 1 || score == 10) {
            list.add(score);
        }
    }
    return list;
}
``` 

It's hard to reuse the previous method, without using interfaces, only because a small change, 
we are comparing by equality (==) instead of bigger than (>) and we can't pass a number as the parameter. 

And **we are duplicating code**, 
the code for looping is repeated because it's really hard to extract because the filtering condition is **inside** the loop.  

Let's see this contrived example with streams:

```java
passed = scores.stream().filter(x -> x > 4)
    .collect(Collectors.toList());

// or

Predicate<Integer> excellentScores = x -> x == 1 || x == 10;

excellent = scores.stream().filter(excellentScores)
    .collect(Collectors.toList());
```

Yes, I've cheated and used a functional interface. But **the point is that you are now only responsible for 
creating the logic to filter the collection** but the stream is the one who iterates, it just need the filtering logic. 

In internal iteration your code is **less coupled with the iteration code**, you don't have to repeat the looping code. 
You are also not in control of the iteration, you don't know if the stream is going to use a temporal variable 
like we did before, and iterator or a for each. 

In an internal iteration, the compiler/library is responsible for the iteration and can:

* Execute the loop in a different order if it makes sense for performance/whatever reason.
* Parallelize the code if we specify it, independently of our code.
* Abstract us from temporal variables, accumulators... we can apply advanced, higher level, transformations like *reduce*, *groupBy* without having to create variables ourselves.
* Merge transformations and loops, if we are applying several filters and transformations, the compiler can optimize them and execute only 1 loop instead of several.

**External iteration is more flexible** (you code whatever you want) but also forces us to implement everything ourselves 
and it's more coupled. **Internal iteration is smarter**, it does the iteration for you and takes care of whatever it needs 
(storing values, escape conditions, accumulators...).

Another good example of the power of internal iteration exists in [jQuery](https://css-tricks.com/lodge/learn-jquery/10-explicit-vs-implicit-iteration/).
When you query for a class or another selector and apply an operation (like changing a CSS class) you don't have to change your code if the query returns 1 or n elements.
The method works for whatever number of elements, jQuery is the one responsible for iterating (if needed) and you just have to provide the code you want to execute.

### Other differences between internal and external iteration

In external iteration, the code **consuming the value has the control** and works better the hardest part is consuming the value. 
In internal iteration the code generating the values is in control and works better when generating values is harder than consuming.

There are some algorithms that are harder to implement with internal iteration and vice-versa, this 
[article](http://journal.stuffwithstuff.com/2013/02/24/iteration-inside-and-out-part-2/) explains all the drawbacks of both approaches. 

## Push vs pull and Lazy vs eager

I'm out of time, so we'll see the differences in the next post! :D

#### Postdata:

I know that, in the Java code, we could have reused the iteration with code similar to this: 

```java
private static List<Integer> filterScores(List<Integer> scores, Predicate<Integer> predicate) {
    List<Integer> list = new ArrayList<>();
    for (Integer score : scores) {
        if (predicate.test(score)) {
            list.add(score);
        }
    }
    return list;
}
```

But that's not the point. What happens if we want to apply another condition? or get the sum of the scores instead of a list? we would have
to modify the method, create a new one or abstract it to work with several conditions (one to filter, another to sum). In the end, the loop code will end up repeated somehow.

With internal iteration, all those transformations can be applied without having to repeat code or create a very abstract method that does too many things.
