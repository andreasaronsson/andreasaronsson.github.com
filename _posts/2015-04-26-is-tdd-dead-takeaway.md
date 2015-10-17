---
layout: post
title: "Is TDD dead takeaway"
description: ""
category: programming
tags: [software,TDD]
---
{% include JB/setup %}

Watching (again) the
[discussions about TDD](http://martinfowler.com/articles/is-tdd-dead/) and
subsequent [presentations](http://www.infoq.com/presentations/tdd-original) and
pondering them for a while I have reached an important conclusion for how I
should regard my own reactions and thought patterns. I have come to realize that
being prepared to throw away code without giving it a second thought is a
**Leading Behaviour**. Naturally this is only the cases where the code and the
features it brings can no longer be motivated by the existence of requirements.

What took longer time without me realizing it what that the same applies to
tests. Let's say I have written tests that give me a healthy dose of confidence.
Then I can change things and be quite certain that I didn't break anything.
During implementation a test that tests *how* code is doing something is quite
handy in many cases. It can help you write the code faster. However, as soon as
the functionality is verified it instead becomes an impediment. We are no longer
free to change the code. Maintainability and ease of change is paramount. It
makes sense to delte these tests. Only keep tests that verify a behavior outside
in, keeping implementation details a secret from the important tests. Preferably
this will not reduce code coverage but if it does in places it is a price we
should be prepared to pay.

{% include share.html %}
