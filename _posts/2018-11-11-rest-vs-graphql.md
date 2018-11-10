---
title: REST vs GraphQL
date: 2018-11-11T10:00:00+00:00
author: nhpatt
layout: post
guid: http://nhpatt.com/rest-vs-graphql
permalink: /rest-vs-graphql/
image: rest-vs-graphql.png
categories:
  - REST
  - GraphQL
  - APIs
---

I owe several posts about the REST books and articles I've been reading lately. But this week [Jorge Ferrer](https://twitter.com/jorgeferrer) shared two interesting links about the never-ending debate about REST vs GraphQL.

I'm pretty tired about talking about it and reasoning about how both, REST and GraphQL, are tools and, as tools, there are sometimes that makes more sense to use one or another. 

*Every other week* someone in the company talks about how it makes more sense to invest in GraphQL instead of rebuilding our REST APIs (just this week we knew there are 3 (!) GraphQL initiatives running around).

Also, Jorge and JM talked about the topic in this [talk](https://2017.codemotion.es/agenda.html#5693168230072320/5069524013416448). I **strongly recommend you** to watch it. They explain the issue and the advantages of one or another better than I could do.

But, back to the topic, I wanted to analyze the 2 links comparing REST and GraphQL.

One is this [talk](https://www.youtube.com/watch?v=yLf0rIaRtRc), **REST vs. GraphQL: Critical Look**.

# REST vs. GraphQL: Critical Look resumed

And these are the things I want to point out of the talk:

* REST & GraphQL are **completely** different things. One is an architectural style (a set of constraints) and the other is a  framework. Both are used to build APIs. But one is way more prescriptive than the other... so we arrive at "So-called REST", another solution that applies partially the set of constraints prescribed by REST.

The constraints of REST get you advantages... decoupling implies that your APIs will be more evolvable, being stateless allows you to get scalability for free or applying a uniform interface gets you simplicity.

So what are the main advantages and disadvantages of both (or 3, with So-called REST) approaches:

* REST is super hard to get it "right" but if you do you get scalability and evolvability. Huge entry barrier, no tooling and very challenging to keep consistency and governance.
    
* So-called-REST applies stateless, cacheable, layered and uniform interface and forgets HATEOAS and self-descriptive messages. With the tradeoff, they lose simplicity and evolvability.
    
* GraphQL, really easy to start, it's like remote data access, a kind of vender agnostic SQL for webs. You get a lot of "Bikeshedding", things that you have to build from scratch: auth, content negotiation, pagination. And also scalability issues. And limited support for other media contents. And more coupling, you have to watch for query optimization.

Whatever you chose, **you don't evade API design**. You have to sit down and think about the shape of your API. It's the first thing you have to do when building a REST API and you can defer it with GraphQL until you see which queries your users are doing (but do it then, you have to optimize them!).
    
The talk points out something I firmly believe. **GraphQL makes more sense if you are talking to yourself**, like building the frontend and backend. If you are exposing a public API that can be used by hundreds of developers... either you are facebook with infinite scaling or prepare your servers for a bad time.

And the other thing I wanted to comment is this [tweet](https://twitter.com/kellabyte/status/1059970357430341632) with 2000 likes (!):

    "GraphQL exists because JavaScript developers finally realized HTTP API’s were too limiting so they reinvented SQL over JSON because JavaScript developers are obsessed with reinventing everything into JSON API’s."

Is GraphQL just a middleware then?