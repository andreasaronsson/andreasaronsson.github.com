---
layout: post
title: "Developers perspective on predictability and velocity"
description: ""
category: programming
tags: [agile,programming,work]
---
{% include JB/setup %}

Being agile means working towards being predictable and being fast. Repeated
measurement are a prerequisite for progress over time. An interesting thought is
that without measuring predictability and speed accountability remains a mirage.

# Predictable

Optimum is to be able to tell in a short amount of time; minutes or days when a
feature is ready. Worst case is to promise to deliver a features and then
breaking that promise. It is easy to end up in a perpetual lie where each
promise is done in earnest. When the team then fails to deliver in time it has
no repercussions.

## Measuring predictability

The team need a data series over comparisons between prognosis and outcome.

# Fast

A feature is done when it works in production without interruptions. Granted
there are vast possibilities to interpret things. It is important to decide what
is in scope and what is not. Success is when there is an agreement between the
consumer and the producer. The negotiating skill will play an important role.

## Measuring how fast

Simple in theory if you have engaged stakeholders and all features are of equal
size.

# The road there

One way to improve is to adopt a zero defect strategy. This means that the team
does not tolerate any outstanding issues (reported bugs or the like). They are
promptly dealt with. Decide if it is worth the investment. If not clearly
communicate this at the earliest opportunity. Decide if it is a bug in existing
features or new functionality. If it is a bug drop planned work and fix it. Else
put in backlog and prioritize.

A second way is to measure and adress build problems. This can be failing builds
on any level (component, integration and system tests). Count the incident rate.
Then adress the ones that occurs most often first. It can also be execution
time. Mixing integration testing with the step where the binaries are created is
a common cause.

A third way is to keep things tidy. Make sure documentation is built with the
product and updated. Remember to update or enhance the documentation whenever
there are questions from users or the team itself. Eradicate warnings and errors
in the build logs. Make ample use of static analysis to help find flaws and
adress them as they are discovered. The earlier the better.

Finally there can be architectural flaws as the underlying cause for all of the
above. As soon as possible attempt to adress these flaws. Be careful to have
enough experience to have high confidence in proposed improvements. For larger
changes this is even more important.

All this requires a hefty amount of discipline. Keep in mind that your
responsibility is to maximize the output for the team in a year from now. This
means it can be pragmatic to take a shortcut at times. However, it is hard to
estimate when the shortcut is worth taking. Extremely hard since the amount of
information about the future drastically shrinks the further into the future one
tries to foresee. This makes the prospect high risk and should not be taken
lightly.

# References

https://www.thoughtworks.com/continuous-delivery
https://www.cprime.com/resources/what-is-agile-what-is-scrum/

{% include share.html %}
