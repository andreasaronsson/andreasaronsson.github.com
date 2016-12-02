---
layout: post 
title: "Programming across borders" 
description: "" 
category: programming
tags: [software,programming,typing,complexity]
---
{% include JB/setup %}

In our new reality change happens faster and faster. This puts pressure on programs and systems to adapt to change. Building blocks become ever larger to help meet expectations on feature deliver rates.

Using as small as possible least common denominators like standard libraries and the types defined there puts a healthy pressure on the semantic intricacies that needs to be communicated. Surprisingly often one can get the job done with less. An interesting mental model to aim to emulate is the mouse with one button or

One consequence is that large monoliths are becoming less common. A corollary of this is that developers write smaller programs more often. What follows is the number of boundaries increase. We need protocols and API's to share information.

A [protocol](https://en.wikipedia.org/wiki/Communications_protocol) is a system of rules that allow two or more entities to communicate. Simplicity in these rules is an advantage. It is desirable for efficiency at scale to make the system usable and easy to change. The amount of effort needed to understand the rules and implement them needs to be small.

Abstractions like user defined types can be a way to enable code reuse. It can limit the number of ways to do a certain operations and make it harder to make mistakes. Abstractions can model the domain and document code. Using a compiler capable of providing a [sound type system](https://en.wikipedia.org/wiki/Type_system) the usage can prove efficient. Sometimes these abstractions comes from a third party like an open source library.

When programs transmit information over a protocol the compiler is not there to help. This means that each type or abstraction must have a representation. The representation must follow the rules. This requires translation. When data reaches the receiving end translated back to the original form. These translations can become cumbersome and are good candidates for automation and code generation. Even when using code generation and automation. The translated representation will often require more data transmission in the end.

Communication is important to do well. Being succinct can be hard but it has benefits. Adding a third party library types to a programmatic API will in most cases force the user to also adopt this library. Transmitting more data will affect performance and possibly saturate network connections.

It is good to put a healthy pressure on the semantic intricacies. Using as small as possible least common denominators helps. These can be standard libraries and archetypal types. Surprisingly often one can get the job done with less. An interesting mental model to aim to emulate is the mouse with one button or [less is more](https://en.wikipedia.org/wiki/KISS_principle).

{% include share.html %}
