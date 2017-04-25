---
title: About Legacy Code
date: 2016-08-29T11:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/about_legacy_code
permalink: /about_legacy_code/
image: about_legacy_code.gif
categories:
  - cylicon valley
  - talks
  - software development
  - legacy code
---

Some months ago I gave a talk about the famous Michael Feathers book, [Working Effectively with Legacy Code](https://www.goodreads.com/book/show/44919.Working_Effectively_with_Legacy_Code).

Here are the [slides](https://speakerdeck.com/nhpatt/working-effectively-with-legacy-code) and the [video](https://www.youtube.com/watch?v=FngQw5KYXK0).

I didn't love the book (even after the second reading), some reasons are explained in the talk but I'll try to describe a few. 

One of my main gripes with the book is that is too focused on testing and that focus is a turn-off for a lot of programmers. 

Nowadays (even in languages like JS) there are a lot of *safe* refactorings with your IDE that could help when dealing with a legacy project. 
The book explains several strategies that do not need tests (and I find those chapters quite interesting) but most of the chapters talk about how to write tests or change the code to allow testing. 

The chapters overlap a lot with *Refactoring* and the specific refactors are better explained there.

I also think that this book is marketed (in hackernews/stackoverflow circles) as a magic recipe to solve legacy projects and, as we already know well, there are no silver bullets and everything needs hard work. 

So a brief summary of the book could be: 
  
* Break dependencies
* Write tests
* Refactor

I recognize that "use common sense and common refactorings" isn't easy to understand or execute but I was one of those expecting something new in this book.
