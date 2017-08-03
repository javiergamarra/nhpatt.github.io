---
title: I've read... Restful Web Clients
date: 2017-08-02T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/read_restful_web_clients
permalink: /read_restful_web_clients/
image: read_restful_web_clients.png
categories:
  - rx
  - reactive
  - development
---

A quick post before continuing with Rx and laziness on Sunday...

I've recently read [Restful Web Clients](https://www.goodreads.com/book/show/34510579-restful-web-clients), by Mike Amundsen, of REST fame.

We (Alex and me, mainly) are developing a Hypermedia producer/client for Liferay and this book inspired some of the work in the producer before I joined the effort.

The book seemed like a great fit for the client project because it basically covers how to develop a client with 
hypermedia from the scratch... but in the end, it wasn't as interesting as I thought.

Don't get me wrong, the book is **thought-provoking for someone that doesn't know anything about hypermedia** (as myself) because the explanation
about *why* hypermedia is important and how we are just using a small part of the theory or ideas behind REST are very interesting.

But the rest of the book (and I mean the 80% of the book) is an explanation about a hypermedia format (HAL, Siren, and Collection+JSON) and how to implement them in bad
javascript and HTML. I definitely didn't need to read the full code, I would have preferred the main concepts (define a loop) and some recommendations or focus on the most tricky parts
and leave the code for the repository. 

## Gripes with the book

I felt that the book didn't have much apart from the hypermedia and formats explanations (that were great and I definitely understand the pros and cons of each format) but that's all.
I don't think I know much about restful web clients right now or how to implement them apart from some small concepts.

I also feel that all the solutions have too much code. It's nice to have a *representor* pattern (strategy) that lets you create several representations of your data in the different
hypermedia formats but also means a lot of code to convert back and forth the intermediate representation. 

I hope no-one encounters the same situation of the book, implementing the full code for the producer and client for 4 or 5 different JSON formats.

## Final words

I've rated it 4 stars of 5 in Goodreads. Yeah, I know. 

But I didn't know the hypermedia formats and why there are important and the **OAA challenge** (support updates and information about Objects, Actions, and Addresses) was nice.

If you already know HAL, Siren or Collection+JSON, skip this one.
