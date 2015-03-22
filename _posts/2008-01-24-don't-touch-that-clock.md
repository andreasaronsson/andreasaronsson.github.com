---
layout: post
title: "Don't touch that clock!"
category: sysadm
tags: [hardware, Gentoo, cooling]
---
{% include JB/setup %}

Time goes by and sometimes gentoo hands you a new update to kde-base as happened today and it's compile-time again. When I first
began using gentoo I sometimes watched the scrolling lines and kind of get stuck much like watching a burning fire. It would give a
cosy feeling and time flew by. Nowadays I never do that for some reason, I just want to be done with it. Having invested in a
[Reserator](http://www.zalman.co.kr/eng/product/view.asp?idx=63), I thought I'd make good use of it and hence overclocked my
CPU. Well, the speed increase was hardly noticeable but the temp never exceeds 40 degrees C anyway so I thought I might just let the
CPU running at 2200MHz instead of 2000. I read somewhere that overclocking could give you all kinds of unforeseen
problems. Indeed. First thing I noticed was that the system clock went way off. "Clock skew detected" when I compiled my
programs. This because my /home is mounted over NFS, and the server isn't overclocked. A quick and dirty ``while true;do
/etc/init.d/ntp-client restart;sleep 200;done`` in a screen made the annoyance go away that day. The problem persists of
course. Next, the sound in amarok starts stuttering! It's like a hiccup with 2-3 seconds interval. Recompile of amarok, alsa-lib and
xine-lib does not help. I whip up alsamixer to see if something has been changed. No avail. Reboot, and remove the overclock. Now
the soundcard is even worse, and the left channel is dead altogether. Messing around with the alsamixer again seets the soundcard
straight by messing with the "Multi Track Internal Clock" and now it's playing nicely. The system clock's still on it's own track
though. Not sure if I'm out of battery on my ASUS A8N-E and I have preciously had some trouble with the ice1724 driver for my
soundcard but I really think I'm better off without overclocking anyway =).

{% include share.html %}
