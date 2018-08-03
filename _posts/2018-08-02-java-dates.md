---
title: Java Dates
date: 2018-08-02T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/java-dates
permalink: /java-dates/
image: java-dates.png
categories:
  - JSR-310
  - java
  - dates
---

Today I gave an internal talk about the *new* java dates introduced in Java 8, the JSR-310 spec. Obviously, given that
I recycled some slides of a [talk](https://docs.google.com/presentation/d/1nCnlI4riLETsgLfjFnWljyTQacwQur8_4VZ_DvwgPxo/edit?usp=sharing) I gave in 2013, there are not really new. But few people are using them.

I really like the API of [LocalDate](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDate.html), being immutable and [TemporalAdjusters](https://docs.oracle.com/javase/8/docs/api/java/time/temporal/TemporalAdjusters.html) are really nice, those are things where I've 
struggled with the old Date/Calendar API before (especially trying to calculate "the third Monday of the month").

So maybe it's useful for you too, **here are the [slides](http://bit.ly/310dates) and the 
[repository](http://github.com/nhpatt/evolution_of_java)**.

The talk went Ok. I didn't prepare it a lot in advance (I just created the slides and the tests) but it's an easy topic to 
talk about. But it was nice to have the slides done days before the talk :P

Feel free to contact me on [twitter](https://twitter.com/nhpatt) if you notice an error or have a suggestion :)