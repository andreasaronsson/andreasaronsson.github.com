---
layout: post
title: "Disc fest II"
category: hardware
---

Finally had time to finish all my data migrations with the new discs. 

The original setup was (tip: use ``smartctl -i /dev/sdX`` to get the disc info): 

* Box one (workstation) - one wd raptor GD (one gentoo partition, one windows).
* Box two (server) - one wd raptor GD (running mail, web, domain etc) and one IDE disc
* Box three (fileserver and offsite backup) - three IDE discs with


the system spread out on a RAID1 and all the remaining disc space
crammed together in a logical volume for my picture collection.

Final setup:

* Box one (workstation) - one wd raptor ADFD</li>
* Box two (server) - two wd raptor GD and two IDE discs, both RAID1
* Box three (fileserver and offsite backup) - two SATA discs in a RAID1

I didn't have any major breakdowns or hiccups but still some interesting stuff happened. In both servers I made heavy use of ``rsync -a --exclude xxx source dest`` from the running system to the new disc setup. However, the first procedure moving all the stuff off of the file server was hampered by one of the discs in the logical volume. 
It decided to die in the process. I haven't thought much of it thus far but for some reason they always seem to break when you touch them. The can go on spinning happily for weeks on end but if you reboot or look at them too closely all hell break loose. So I lost some stuff. Shit happens and I probably could have avoided it had I only been a bit less lazt. Yet again I draw the conclusion that arduousness more or less always pays off in the long run. 

The second server I amused myself with syncing the running system (with as much services turned off as possible ofcos) to the new RAID array and the unmounting some of the partitions and remounting the mountpoints with the newly synced filesystem. When I later rebooted and proceeded to incorporate the first disc in the array, I discover that the disc seems to be in use. ``sfdisc -d /dev/sdb|sfdisc /dev/sda`` does not go succeed even if I use --force! 
"Device busy". Intriguing! After some rummaging around an ``lsof /dev/sda3`` gives me loads of open files as if 
I was still running a system on this disc. As this is not the case I am still kinda stumped about it. 
Tomorrow it's Friday. That means more time to investigate what's really happened to my root partition. 
I plan to add that one as well to my root RAID device. 

By the way, I'm typing this in emacs, then using org-mode to export it in html format. I think it's really neat.  
