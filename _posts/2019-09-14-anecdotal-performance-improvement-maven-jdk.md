---
layout: post
title: "Anecdotal performance improvement maven jdk"
description: ""
category: code, programming
tags: [programming, maven, java]
---
{% include JB/setup %}

Looking through [this presentation on performance enhancements jdk 8 through 13](https://cr.openjdk.java.net/~redestad/slides/lean_mean_openjdk.pdf).
And [these release notes for maven-3.6.2](https://maven.apache.org/docs/3.6.2/release-notes.html).
I was inspired to see if jdk12 and maven-3.6.2 made any difference over jdk11 and maven-3.6.1.
A minimal project and `mvn validate`.
The average build times went from about 0.45 to 0.30.
There is of course a wide variety of other things to measure using many other methods.

{% include share.html %}
