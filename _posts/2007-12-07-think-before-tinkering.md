---
layout: post
title: "Think before tinkering"
category: sysadm
tags: [grub, raid]
---
{% include JB/setup %}

It was too obvious for me this time perhaps. I simply forgot to change grub's
arguments from the disc to the RAID1 device. Now I can continue to expand my
logical volume across both partitions and add the remaining root partition to
the RAID as well. That's what sleep deprivation will to to you. OR that's what
you get for not thinking first. I have discovered that it is very useful, be it
programming or sysadmin projects, to make sure you build a path in your mind
made up of pictures or visualisations of what you are trying to achieve. Much
like the route you take to work; walk a bit, drive a bit, walk a bit more, open
the door... You make it clear enough for you inner eye to be able to walk it in
its entirety and clearly see the details. The first time I discovered I had the
ability to do this was a profound experience. Really. Yes, I'm a nerd and it
means this much to me. I'll say it again, if not just to remind myself as I was
too much in a hurry to do it this time; think before tinkering.

{% include share.html %}
