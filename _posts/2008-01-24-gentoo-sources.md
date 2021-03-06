---
layout: post
title: "Gentoo-sources"
category: sysadm
tags: [linux, Gentoo]
---
{% include JB/setup %}

I have to say my impression is that the gentoo devs maintaining the kernel sources does a damn fine job.
New versions appears in the three at a very nice rate and keeping up with the relentless pace of vanilla.
At the time of this writing the latest stable kernel is 2.6.23.14 and portage just gave me 2.6.23-gentoo-r6.
Good stuff.
I've been compiling gentoo-sources for a few years now and it has never been smoother.
A simple

``emerge -Nqa world``

* copy the old .config to the new source dir
* swap the symlink

``make oldconfig``

Then run my dead simple shell script:

{% highlight bash linenos %}
#!/bin/sh
mount /boot
cd /usr/src/linux
make && make modules_install
mv /boot/bzImage /boot/bzImage.bak
cp /usr/src/linux/arch/x86_64/boot/bzImage /boot
cp /usr/src/linux/.config /boot/dotconfigurebackup
cp /usr/src/linux/System.map /boot/System.map
umount /boot
{% endhighlight %}

This was created prior to reading [Diego Penetto](http://farragut.flameeyes.is-a-geek.org/articles/2007/11/02/why-people-insist-on-using-boot) with which I agree and future setups will follow that.
Next, reboot.
Very much hassle free, almost too good as the main reason my choosing gentoo is to learn stuff ;-).
The smooth operation and this interesting read: <http://www.gentoo.org/proj/en/kernel/maintenance.xml> makes me even more keen on gentoo.
[dsd](http://www.reactivated.net/weblog) really seems to 'get it'.
The more the merrier and he certainly contributes in a positive manner.

{% include share.html %}
