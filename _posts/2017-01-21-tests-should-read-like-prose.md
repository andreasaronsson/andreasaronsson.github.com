---
layout: post
title: "Tests should read like prose"
description: ""
category: programming
tags: [software,programming]
---
{% include JB/setup %}

Expressing solutions to problems is at the heart of programming.
Cognitive load slows you down.
Not using natural language adds to the cognitive load.
Writing software benefits from using natural language.
This is something I think of very often in my work.

When using [JUnit](http://junit.org/) I use the Junit4 API `assertThat` whenever possible.
This enables me to write

```
assertThat(result, is(expected))```

Compare this to Junit3

```
assertEquals(expected, result)
```

Junit5 is in development.
It surprised me to see that they are using what I perceived as "Junit3 syntax".
In the
[user guide](http://junit.org/junit5/docs/current/user-guide/#third-party-assertion-libraries)
we find the explanation.
The `assertThat` API is reserved for third party assertion libraries like hamcrest or assertj.
The more powerful API is open to extension and pluggable.

An excellent choice.


{% include share.html %}
