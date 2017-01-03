---
id: 1185
title: Brief notes about JS
date: 2015-06-08T12:00:40+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/brief-notes-about-js/
permalink: /brief-notes-about-js/
categories:
  - dev
---
El pasado miércoles un par de amigos se acercaron a hablar de típicos _pain points_ de Javascript, os dejo las notas que tomamos. No pretende ser una guía de estilos (que hay unas cuantas en la red). Si detectáis algún error o discrepáis, **comentad**!

# Brief notes about JS {#toc_0}

## Idiomatic JS {#toc_1}

  * Use always `[]` instead of `new Array()`
  * Create objects with `{}`
  * Set a default value with `||`, for example:

    ```javascript
    var number = something_that_could_be_undefined || 0;
    ```

  * Check if array is not empty with `if (array.length) {...}` or empty with `!array.length`.
  * &#8216;Double negation operator&#8217;: `!!variable` to force a cast to boolean.

## Useful constructions {#toc_2}

  * Module pattern, a way of having _private _methods and properties. Typically similar to: `(function() {} return {})()`. A function that is being executed instantly.

  For example:

```javascript
    (function module_pattern_revealed() {

        var private_element = 2;

        function example_function() {
            operate_with_private_element
        }

        return {
            example_function: example_function
        }

    })();
```

  * Understanding `prototype`: every object is linked to a prototype object from which it can inherit properties. This is done dynamically, so you can decorate `language objects` like `Array` or all your own objects at the same time.

  * Closures: functions can be defined inside of other functions. An inner function of course has access to _the parameters and variables of the functions it is nested within_.

    The function object created by a function literal contains a link to that outer context.

    This is really powerful and can be the origin of strange behaviours with loops and event handlers if not understood correctly.
  * Truthy and falsy: a lot of values cast to false, like undefined or 0, so in JS we talk about `truthy` and `falsy`values (those who cast to true or false, respectively).

  * Hoisting: variables and functions are moved to the top of the scope in which are defined.

## This&#8230; {#toc_3}


We have 4 ways of invoking a function:

  * Method invocation, `this` is the scope of our object.

```javascript
    var myObject = {
        value: 0,
        increment: function (inc) {
            this.value += typeof inc === 'number' ? inc : 1;
        }
    };

    myObject.increment();  // 1
    myObject.increment(2); // 3
```



  * Function invocation, where `this` is the scope of the &#8220;global&#8221; object (window in a browser).

```javascript

    myObject.double = function () {
        var that = this; // Workaround.
        var helper = function () {
            that.value = add(that.value, that.value);
        };
        helper(); // Invoke helper as a function.
    };

    // Invoke double as a method.
    myObject.double( );
```
    
`helper` is invoked as a function and `this` refers to the global scope. The usual workaround is use a variable called `that` or `self` that &#8220;caches&#8221; the value of `this`.

  * Constructor invocation, `this` refers to the scope of our object

```javascript

    var Quo = function (string) {
        this.status = string;
    };

    Quo.prototype.get_status = function () {
        return this.status;
    };

    // Make an instance of Quo.
    var myQuo = new Quo("value");
    myQuo.get_status() // value
```

  * And use `bind`, `apply`, `call`&#8230; where the programmer sets the value of `this`.

The only _strange_ behaviour is calling a function with a function invocation (constructor and method works fine).

The bad case is more common as it seems, because _event handlers_, _DOM events_, _timeouts_ or other corner cases.

The solutions are:

  1. Understand why `this` behaves this way and react accordingly.
  2. Program only using properties, constructors (without forgetting `new`) or use apply (and derivates).
  3. Create variables like `that`.
  4. Don&#8217;t use `this` ever.

### References {#toc_4}

  1. Examples from `Javascript: The Good Parts`