---
layout: post
title: "Don't extend"
---

As I am nowadays using the keyworded gentoo-sources, I am already using the 2.6.29 kernel with promised updated ext4 stuff and some more goodies. However, after doing my normal upgrading routine with make oldconfig and sifting through all the new options, running my 'build kernel and drivers'-script, my system wouldn't boot =|. Unable to remount read-write dmesg said. A wee bit stumped, I went back to 2.6.28 for a few days but now I had a go again and took a look at my fstab. In the mount options, I had put "extents, barriers=0". Not sure why since none of the threads I found with google made those options look very promising. Particularly, when I found a note about deprecating extents, I figured thay have to go.  Said and done, I have now booted with little devils peeking at me from the screen instead of penguins. I might have noticed a very slight speedup when starting programs too. 
Ah, portage tells me it's time to go xorg-1.5. Now where did I put the bookmark for the upgrade guide...
