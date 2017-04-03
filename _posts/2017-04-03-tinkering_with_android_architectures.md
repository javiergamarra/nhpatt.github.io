---
title: Tinkering with Android Architectures
date: 2017-04-03T11:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/tinkering_with_android_architectures
permalink: /tinkering_with_android_architectures/
image: tinkering_with_android_architectures.png
categories:
  - cylicon valley
  - from the trenches
  - events
  - android
---

Two weekends ago I gave a talk about the orientation "problem" in Android and how it 
has affected the design of an SDK that I'm developing.

The SDK part was an excuse to talk about restrictions, in particular the architectural 
restriction Android imposes to the developers when dealing with lost state, 
the possible memory leaks, the duplicated requests... and the restrictions when creating a 
library or an SDK, a topic I'm a bit obsessed with.

Don't expect nothing fancy, it's an entry level Android talk to divulgate about specific android issues. 
The slides are available [here](https://docs.google.com/presentation/d/1D1luP-ouXR4zFJtfOdGd52NOIOrrSG4Wn0OP2IJL1lM/edit?usp=sharing) 
 and this is the video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/fgxq3skrdDQ" frameborder="0" allowfullscreen></iframe>

I don't like the current architecture of the SDK, even when I'm the person responsible of
it. 

I do think it's better than it was before and I have lots of ideas to improve it further... 
but I also think it's not important right now. There are other priorities and spending more time 
on it feels like focusing too much on the code side and ignoring the business.

Any suggestions are welcomed, though :)