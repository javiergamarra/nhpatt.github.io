---
title: Internal, push and lazy II
date: 2017-08-13T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/internal_push_and_lazy_ii
permalink: /internal_push_and_lazy_ii/
image: internal_push_and_lazy.png
categories:
  - rx
  - reactive
  - development
---

Continuing with the [previous post](/internal_push_and_lazy), where I talked about the differences between internal and external iteration, today we are going to
discuss what it means for Rx (or Java8 Streams) to be *lazy*.

## Not so lazy evaluation

Streams (Rx or Java) **are not executed until a terminal operation is called**, it can be a *collect* method in Java8 Streams or a *subscribe* in Rx. 

All the operators
we apply to our event source are not evaluated if we don't call those terminal operations. That way we can express our intention, a sequence of actions, without executing it.
That's one type of laziness. But **it isn't the one we are going to discuss today**.

Let's see a javascript example. We want to filter the business trades (*movimiento de acciones* for my spanish followers) of IBM in the global exchange. Specifically, we want
the first trade involving over 1000 options for new IBM stock.

```javascript
for (const trade of trades) {
    if (trade.quantity >= 1000 
        && trade.issuer === 'IBM' 
        && trade.status === 'new') {
            return trade;
    }
}
```

This code has some drawbacks. First, it's hard to parametrize (what happens if we want to filter for IBM **and** MacMillan Utility?). And second, it's strange, we are looping but exiting the loop
early (*short circuiting operation*). We can do it in a function but if we are inside a function we should do a *break* or use a variable (ugly!).

One, naive, approach to allow parameters would be extracting the filtering to functions, like this:

```javascript
function filterByQuantity(trades, quantity) {
    let filtered = [];
    for (const trade of trades) {
        if (trade.quantity >= quantity) {
            filtered.push(trade);
        }
    }
    return filtered;
}
```

This is not very idiomatic javascript code but would be common in Java. We can do it better for the next function:

```javascript
function filterByIssuer(trades, issuer) {
    return trades.filter(x => x.issuer === issuer);
}
```

Looks better! And we could apply several filtering functions like this sequence:

```javascript
const bigTrades = filterByQuantity(trades, 1000);
const ibmTrades = filterByIssuer(bigTrades, 'IBM');
const newTrades = filterByStatus(ibmTrades, 'new');

console.log(newTrades);
```

But our last function, with the short arrow syntax, has also a very big drawback. It's not short circuiting! It's traversing **all** the elements
 and returning all that trades that passes our check and we just need the first one.
 
Luckily ES2015 (not so luckily for IE users) added a function that returns the first element that passes the check, like this:

```javascript
function filterByStatus(trades, status) {
    return trades.find(x => x.status === status);
}
```

We can't use our *find* method in the previous functions because the first big trade could be a Microsoft trade or an old trade.

Ok, let's recap. The first approach with a temporal array is quite common in Java (because collections don't have *filter*) but verbose. 
The second approach is Ok but is traversing all the elements in the array. And the third approach is great for our use case but doesn't work in Internet Explorer.

We could also write it this way:

```javascript
const trade =
    trades
        .filter(x => x.quantity >= 1000)
        .filter(x => x.issuer === 'IBM')
        .find(x => x.status === 'new');
```

Or extract the functions to lambdas... 

But all these approaches have a serious flaw that Rx (Java or JS) and Java streams do not have. Let's see how can improve our code. 

## Lazy evaluation

We could use RxJava, RxJs or Java streams to show this new approach. We are going to use RxJS. But first, we have to know what we can improve!

Let's add a console.log in each of our filtering steps of the last example. This what is was logged:

```
quantity: {"quantity":1300,"issuer":"IBM","status":"new"}
quantity: {"quantity":300,"issuer":"Microsoft","status":"old"}
quantity: {"quantity":2100,"issuer":"IBM","status":"new"}
issuer:   {"quantity":1300,"issuer":"IBM","status":"new"}
issuer:   {"quantity":2100,"issuer":"IBM","status":"new"}
status:   {"quantity":1300,"issuer":"IBM","status":"new"}
RESULT:   {"quantity":1300,"issuer":"IBM","status":"new"}
```

We are iterating all the elements to filter by quantity, then just the 2 ones that have that quantity and then only the first one.

If we implement it with RxJS, this would be the code: 

```javascript
Rx.Observable.from(trades)
    .filter(x => x.quantity >= 1000)
    .filter(x => x.issuer === 'IBM')
    .find(x => x.status === 'new')
    .subscribe(x => console.log(x));
```

As you can see it's pretty similar to the previous code. And if we log each step:

```
quantity: {"quantity":1300,"issuer":"IBM","status":"new"}
issuer:   {"quantity":1300,"issuer":"IBM","status":"new"}
status:   {"quantity":1300,"issuer":"IBM","status":"new"}
RESULT:   {"quantity":1300,"issuer":"IBM","status":"new"}
```

BAM! What happened? RxJS is iterating and applying **all the filters to the first element** instead of 
each filter to all the elements. 

RxJS is *lazy* in that sense (or short circuiting). It does not check the quantity to get all the trades bigger than 1000 and then look the company.
It applies all the filters to the first element and if it's ok, stops.

Let's see another example with a different source, trades:

```
const trades = [
    {quantity: 300, issuer: 'Microsoft', status: 'old'},
    {quantity: 1300, issuer: 'IBM', status: 'new'},
    {quantity: 2100, issuer: 'IBM', status: 'new'},
];
```

And result:

```
quantity: {"quantity":300,"issuer":"Microsoft","status":"old"}
quantity: {"quantity":1300,"issuer":"IBM","status":"new"}
issuer:   {"quantity":1300,"issuer":"IBM","status":"new"}
status:   {"quantity":1300,"issuer":"IBM","status":"new"}
RESULT:   {"quantity":1300,"issuer":"IBM","status":"new"}
```

RxJS applies the first filter to the first element and fails, so it can ignore that element and continues with the second...

This behavior is not related to the *first* method, it is just **how Rx works**. The elements of the stream go all the way with 
the transformations/operations until we verify the last condition or we process all the elements.

## Why is this great?

Do you remember the first code, the one with the *return* condition?, RxJS is doing exactly that but without implementing 
it explicitly (let's not forget that a *break* is a type of *goto*) and allowing us to extract functions or lambdas easily.

We get **better performance** that the function examples because we only execute the minimum number of operations (or in the worst case, the same) 
but **without losing expressiveness**.

We are used to code that reads sequentially when we apply functions. 
In RxJS we don't loop until we have executed all the stream of operations to the first element. 

It's harder to understand but simply better: expressiveness without losing performance!

## Push vs pull

I'm out of time, so we'll see the differences in the next post! :D
