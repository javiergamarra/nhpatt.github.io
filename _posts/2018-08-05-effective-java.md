---
title: Effective Java
date: 2018-08-05T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/effective-java
permalink: /effective-java/
image: effective-java.png
categories:
  - java
  - book
  - effective java
---

Last week I read the third edition of [Effective Java](https://www.goodreads.com/book/show/105099.Effective_Java_Programming_Language_Guide).
It was of the must-read books stuck in my TO-READ list. **And it was better than I expected!**. 

There were a lot of things I already knew. **Obviously, I should have read it many years ago**, and I wouldn't have fallen into
many mistakes Joshua Bloch mentions in the book. But I've read it now, after 10+ years writing Java programs... and still, there were some
surprises, a fair share of new things!. 

And here it is a noncomprehensive list of the 90 items, the ones that left me scratching my head:

* Item 31: **Use bounded wildcards to increase API flexibility**

The idea is, inside a public API of a library with generics, **expose a bounded wildcard** \<E extends MyDomainClass\> **instead of a generic**, like MyDomainClass.
That way consumers of your library have more flexibility. This applies to classes, methods with input arguments and outputs. There
is even a mnemonic to know which kind of bounded wildcard to use!

I have to say that most items in this chapter about generics taught me several things... especially the item about how
to ignore casts and warnings 😳

* Item 36: **Use EnumSet instead of bit fields**

Ok... I didn't know *EnumSet* existed. Enough said. I was even at a loss on how joining integer constants with \| worked... 

* Item 55: **Return optionals judiciously**

I had already read about the bad practice of using Optional as fields... but I hadn't thought a lot about returning Optionals
in a library and how it forces the users to deal with it. Food for thought.

* Item 69: **Use exceptions only for exceptional conditions**

I also supported it before reading the book but the book made me hate Checked Exceptions even more!

* Item 86: **Implement Serializable with great caution**

I'm not using *Serializable* a lot right now. But I used to do it... without knowing all the problems associated with it 
(I knew about serialization conflicts but not the security problems). After reading 7 or 8 items about Serialization, the book
convinced me to not use it ever again. Eye opener.

...

A quite interesting book, I recommend you to check it out if you already know Java and have a few years of experience with it, 
even if **you only read the chapters/items that you like/want** to learn more.

See you around! :D