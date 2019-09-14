---
layout: post
title: "Single responsibility and function reuse"
description: ""
category: programming
tags: [complexity,java]
---
{% include JB/setup %}

Five basics principles in [OOP](https://en.wikipedia.org/wiki/Object-oriented_programming) is [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))
The first principle is [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle).
One reason to change leads unequivocally to smaller classes in terms of lines of code.
There are many advantages that comes from using this principle.
Classes becomes easier to test.
Classes becomes easier to reason about.
Seeing opportunities for reuse becomes easier.
The way you organize code in packages in Java makes this work.
In a different language where many classes are defined in the same compilation unit or file.
This way a module may contain a smaller number of compilation units / files.
The files on average contain more classes and functions.
Depending on how the information is visualized.
With an IDE classes could be lined up in one view.
In a pure text editor this is much more rare.
This can make it harder to spot opportunities for function reuse.


{% include share.html %}
