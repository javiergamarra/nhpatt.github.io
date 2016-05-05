---
title: Cliques in Android
date: 2016-05-09T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/cliques_in_android
permalink: /cliques_in_android/
image: androids.jpg
categories:
  - android
  - software development
---

There is a word for this, I'm pretty sure.

In a software community (it doesn't matter which one) there are always mantras, things the community consider **true** and repeating them in talks or conversations is a proof of belonging to the group, some sort of an insider joke.

If you are outside the community you don't know those mantras and usually you are taught **just the opposite** in circles outside the community, like universities, non-opinionated books or online courses.

The javascript and ruby communities have several of those mantras, usually modelled in writing *idiomatic* ruby or JS and leading to huge fights about the importance of semicolons.

The Android community has some also, usually grounded on bad API design in the Android core. I consider them **well founded** but I'm a bit afraid of repeating them without **justifying** them.

I find myself discussing them with students, novices in Android or people from other languages and I spend **too much** time sending links about the reasons behind those judgments. So I'm writing down several of those links.

The most important ones (right now) are:

### Async Tasks are **BAD**:

Yeah shocking, I know, if you are **inside**

* Good post of Dan Lew about some of the [problems](http://blog.danlew.net/2014/06/21/the-hidden-pitfalls-of-asynctask/)
* An older [post](http://bon-app-etit.blogspot.com.es/2013/04/the-dark-side-of-asynctask.html)
* A good [recopilation](http://simonvt.net/2014/04/17/asynctask-is-bad-and-you-should-feel-bad/)
* This talk explains some [alternatives](http://www.slideshare.net/flipper83/get-out-of-my-thread-trabajando-en-diferido)

### Fragments should be avoided, if possible:

* The famous post that it started [all](https://corner.squareup.com/2014/10/advocating-against-android-fragments.html)
* A good talk explaining [alternatives](https://speakerdeck.com/rallat/android-development-like-a-pro)

### Event buses should be used with **caution**

Or not at all

* A small blog [post](http://endlesswhileloop.com/blog/2015/06/11/stop-using-event-buses/)
* A good [flame](https://www.reddit.com/r/androiddev/comments/39tq6t/event_bus_is_an_antipattern/)


The best way of staying up-to-date in the alternatives are following the slack community, [reddit](https://www.reddit.com/r/androiddev), conferences and talks...

PD: I'm not against mantras, *per se*. I'm against repeating without understanding the underlying problems :)


> Photo by [etnyk](https://www.flickr.com/photos/etnyk/)