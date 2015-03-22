---
layout: post
title: "OpenRC-time"
category: sysadm
---
{% include JB/setup %}
{% include share.html %}

Finally I made the leap. 
Used the stopwatch to get the boot time from BIOS POST to login screen: 1:02.4
Added 

>sys-apps/openrc ~amd64
>sys-apps/baselayout ~amd64

to ``/etc/portage/package.keywords``
Emerged them and followed the guide: 
<a href="http://www.gentoo.org/doc/en/openrc-migration.xml"></a>

No problemo. New boot time: 
00:48.4
Sweet. Thx Roy! 
