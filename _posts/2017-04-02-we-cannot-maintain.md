---
layout: post
title: "We cannot maintain"
description: ""
category: general
tags: [recruitment,software,collaboration]
---
{% include JB/setup %}

A large organization involves many people working together.
A large and complex product can have many requirements.
Say we split requirements into two categories.
One relates to customers and the core business.
The other consists of functionality that a user can not immediately observe.
These things can be configuration, deployment and logging.

With many teams involved it is easy to spot opportunities for reuse.
Avoid reinventing the wheel.
It is desirable to have a product that is easy to maintain.
Maximising use of available third party libraries is a given in this context.

Two ways are conceivable to achieve this.
Either write your own wrapper that teams must use.
Or provide written instructions for teams to follow.

With a wrapper comes the cost of maintaining the wrapper itself.
This includes maintaining well written documentation.
Teams and new team members needs education on using the wrapper.
In time the third party libraries release new versions.
They can contain new features that makes the product better or reduces work.
Then the maintainers of the wrapper may need to make changes to make the feature available.

With a written instruction use audits to ensure compliance.
Any problems that occur due to non-compliance by teams are bugs.
We can assume that teams consists of talented individuals.
Following a written instruction is an easy task.
Interacting with third party libraries can be easier for a new employee.
Third party libraries with a large user base are likely to be familiar.
They also have on average well written documentation.

When in doubt do not write a wrapper.
It may seem tempting as first glance.
Doing well at communicating instructions can prove a lot more efficient.

{% include share.html %}
