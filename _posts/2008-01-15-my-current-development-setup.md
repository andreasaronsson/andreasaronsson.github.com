---
layout: post
title: "My current development setup"
category: code
---

Inspired by <a href="http://www.briancarper.net">Brian Carper</a> (programming in general) and <a href="http://farragut.flameeyes.is-a-geek.org">Diego Penettó</a> (C/C++), I started configuring a
setup to do some programming on a private project. I decided I'd go for <a href="http://www.eclipse.org">Eclipse</a>, <a href="http://subversion.tigris.org/">Subversion</a> and
<a href="http://trac.edgewall.org/">Trac</a>. First time I single handedly abandon my beloved Emacs. 

Eclipse has got a number of plugins
available. <a href="http://www.eclipse.org/cdt/">CDT</a> and <a href="http://www.eclipse.org/subversive/">Subversive</a> seemed like good choices.
Firstly, setting up Trac and Subversion on the server was a breeze using the <a href="http://www.gentoo.org">Gentoo</a> ebuilds. Sources
are easily browsed in the Trac web interface. Howtos and tips and tricks are swiftly edited into Trac
too.

Next, it was time for Eclipse. This time the ebuild was alot more awkward to work with as the tree
seems to be a tad behind. Soon I switched to manual download directly from the eclipse website  and
installing it in my own home directory. I was pretty stumped to see my system responding to me
issuing "./eclipse" with... nothing. Allmighty Google allowed me to educate myself enough to
understand that this was a common error when you try to run the 32-bit version on a 64-bit
system. As I am running Gentoo on amd64;
<a href="http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20071103/eclipse-jee-europa-fall2-linux-gtk-x86_64.tar.gz">this 64 bit version</a> works alot better.
Now I am having loads of fun rewriting a program I last worked with sometime in 2003. Time flies...
