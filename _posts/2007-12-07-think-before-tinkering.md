---
layout: post
title: "Think before tinkering"
category: sysadm
tags: [grub, raid]
---
{% include JB/setup %}

It was too obvious for me this time perhaps.
I simply forgot to change grub's arguments from the disc to the RAID1 device.
Now I can continue to expand my logical volume across both partitions and add the remaining root partition to the RAID as well.
That's what sleep deprivation will to to you.
OR that's what you get for not thinking first.
I have discovered that it is very useful to visualise what you are trying to achieve.
This is true for programming and sysadmin projects.
Like the route you take to work; walk a bit, drive a bit, walk a bit more, open the door.
You make it clear enough for you inner eye to be able to walk it in its entirety and clearly see the details.
The first time I discovered I had the ability to do this was a profound experience.
So think before tinkering.

{% include share.html %}
