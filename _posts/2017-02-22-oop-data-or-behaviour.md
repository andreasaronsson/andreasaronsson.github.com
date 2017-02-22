---
layout: post
title: "OOP data or behaviour"
description: ""
category: programming
tags: [software,programming,functional]
---
{% include JB/setup %}

I have put a significant effort into understanding [OOP](https://en.wikipedia.org/wiki/Object-oriented_programming).
Years ago I remember thinking that my knowledge was becoming mature.
An important concepts is that data and procedures to manipulate the data go together.
Applying the principles in my daily work made me reconsider some aspects.
One aspect that I started to use was to do the opposite.
Classes contained data *or* procedures.
Actually not as clean cut as that but rather that I created two kinds of classes.
One kind I tried to make as dumb as possible.
Free from logic.
Data and accessors only.
The other kind had logic.
I wrote tests for both kinds.
The kind that contained data wasn't very interesting to test.
We tested them anyway to please the coverage metrics gods.

A handful more years have passed since then.
I have delved deep into the realms of functional programming.
Today I frown on void methods and methods without parameters.
I am much more picky about making classes members of other classes.
There are many examples of how it has affected the way I think.

Thinking back I realize something.
We may have understood some of these things on a subconscious level.

{% include share.html %}
