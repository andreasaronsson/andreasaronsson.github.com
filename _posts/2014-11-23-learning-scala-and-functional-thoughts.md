---
layout: post
title: "Learning Scala and functional thoughts."
description: ""
category: programming
tags: java,scala
---
{% include JB/setup %}

Incredibly enough it is more than two years ago now I took the [MOOC](https://en.wikipedia.org/wiki/Massive_open_online_course)
Scala course at [Coursera](https://www.coursera.org/)
[Functional Programming Principles in Scala](https://www.coursera.org/course/progfun) and in this text I try to reminisce what the
learning experience was like. 

Looking back now I realize it has affected me profoundly. These days I pick other youtube videos to watch as functional programming
is much more interesting. It has also changed my way of thinking when I write code. As I have become aware of what makes it hard to
reason about the constituents more and more of my energy is spent on these things. The course is highly rewarding and I am sure it
has been improving since I participated. 

When I first saw the syntax I noticed the use of parenthesis instead of brackets as I was accustomed to in Java. My thought then was
'why change that which is not broken'. After studying some more I realized that this was that it followed logically from the fact
that 'everything is an object *and* a function'. Another aha-moment for me was when I was writing tests for the code I has
written. I realized that the tests was really testing the things I was interested in testing. The amount of bolt-and-nut problems
one has to solve when working with a language this elegant is minute compared to what I do in my regular work. Exceptions, nulls and
mutating state even if only for external iteration keeps getting in my way. 

Functional thinking has made such a deep impression on me. However, as always with any tool I use I soon find many things I dislike
about it. The things that prevents me from doing even more Scala today are compile times, weird inconsistencies that probably
follows from putting all kinds of features into the language at a senseless pace. This is highlighted in detail by the mesmerizing
[Paul Phillips](https://www.youtube.com/watch?v=TS1lpKBMkgg). I believe that Martin Odersky is spot on with his plans to
[simplify the language in the coming years](http://www.scala-lang.org/news/roadmap-next). Today it feels a bit like a research
experiment to me. 
