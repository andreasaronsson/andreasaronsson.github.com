---
layout: post
title: "From Gentoo to Arch"
description: ""
category: sysadm
tags: linux
---
{% include JB/setup %}

A while ago I came to realise that I spend way too much time updating
my systems. Doing ``emerge --sync`` etc way too often, especially for
a command that takes so much time to complete. After that it was
usually ``emerge --depclean`` and then ``revdep-rebuild`` to get that
rock solid system I wanted. Simply a bad habit doing it so often
instead of scripting. I have also spent alot of time doing all sorts
of configuration of mysql and postgre, apache, postfix and many other
services. Compiling linux many, many times and trying to make it as
small and lean as possible. In retrospective the work has been quite
repetitive and more of the type of trying to figure out how somebody
else has written a piece of software that one needs to figure out how
it works and what it expects and what assumptions have been
made. Sometimes it is easy depending on how well documented it has
been. Other times it is very time consuming. What I learned over these
years was that it has not been as rewarding. I am spending less and
less time with these things the last few years. Using Arch linux as my
first choice has helped. I am a little less fond of the now almost
ubiquitous systemd. I find it is awkward to use in comparison I don't
think binary logs are the better choice. I can certainly understand
disto maintainers since the amount of packages you need is reduced by
quite a bit. Now I use apper to keep my workstation updated. When I
find the time I might try and find a similar thing for the server
machine. One that does not pull in so many dependencies. 
