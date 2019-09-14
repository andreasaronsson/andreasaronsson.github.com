---
layout: post
title: "My current development setup"
category: code
tags: [programming, Eclipse, emacs, subversion]
---
{% include JB/setup %}

I started configuring a setup to do some programming on a private project.
I decided I'd go for [Eclipse](http://www.eclipse.org), [Subversion](http://subversion.tigris.org/) and [Trac](http://trac.edgewall.org/).
First time I abandon my beloved Emacs.

Eclipse has got a number of plugins available.
[CDT](http://www.eclipse.org/cdt/) and [Subversive](http://www.eclipse.org/subversive/) seemed like good choices.
Firstly, setting up Trac and Subversion on the server was a breeze using the [Gentoo](http://www.gentoo.org) ebuilds.
Sources are easily browsed in the Trac web interface.
Howtos and tips and tricks are swiftly edited into Trac too.

Next, it was time for Eclipse.
This time the ebuild was alot more awkward to work with as the tree seems to be a tad behind.
Soon I switched to manual download directly from the eclipse website.
I installed it in my own home directory.
I was pretty stumped to see my system responding to me issuing "./eclipse" with... nothing.
All mighty Google allowed me to educate myself enough to understand that this was a common error when you try to run the 32-bit version on a 64-bit system.
As I am running Gentoo on amd64; [this 64 bit version](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20071103/eclipse-jee-europa-fall2-linux-gtk-x86_64.tar.gz) works alot better.
Now I am having loads of fun rewriting a program I last worked with sometime in 2003. Time flies...

{% include share.html %}
