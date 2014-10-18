---
layout: post
title: "Creating software in a nutshell"
---

It's been a bit too long since I did a post so I thought I'd post some thoughts about the creation
of software and cooperation in a small group with tools we're using like UML, design patterns
etc. I'm assuming that a sufficiently thorough analysis has been made and that the group comprises
about two to four developers. This would be the optimal course of action for my personal taste and
knowledge level at this time.

<strong>Beginning</strong>

Creating a design in face to face sessions dividing the software into components and then modeling
the parts in UML with an occasional informal sketch not necessarily UML to get thoughts
conveyed. Whatever floats your boat in this regard. It's highly preferable if all devs can retreat
for a while (preferably more than a day), pondering. Pondering includes exercising, writing some
documentation etc. Then the group meets again and continue to flesh out the details.

<strong>Middle</strong>

Individual preferences and consensus are used to divide the work in between developers. Design
patterns are used for discussion thoughts about converting the design into code. They are also used
at leisure in the implementations. Unit tests are being introduced. 

<strong>End</strong>

Implementation details are sorted out. Unit tests are being finished and adjusted as stuff
changes. Documentation ensues and finally for future reference, like when you get new additions to
the group and want to explain the design to them you can generate or change the UML diagram to
reflect changes and additions the group makes during the development process. 

It's probably a rare case when everything is this straight forward and simple, but I think this
would be specific enough to contribute to a discussion and not too heavy but still substantial
enough to help. 
One caveat is that there's a bunch of assumptions about the devs in the group, that they do possess
enough knowledge to be able to do OOA/D, test driven and UML.