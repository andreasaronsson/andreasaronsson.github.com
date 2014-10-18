---
layout: post
title: "Goodbye horde, hello Zimbra"
---

I finally gave up trying to keep my hordeinstallation alive. It's been alot of work installing and upgrading the package and every time I've failed to retain my data. I was recommended <a href="http://www.zimbra.com/">Zimbra</a> by a friend. It turns out it's a complete suite with mta, imap, spam- and virusscanner. This meant that I'd have to give up my carefully configured mail services. After bracing myself for a number of days, I got to it.

Pretty quickly I found an installation method that would enable me to keep my base system and apache installation on their wiki:  <a href="http://wiki.zimbra.com/index.php?title=Building_Zimbra_on_Gentoo">building Zimbra on Gentoo</a>. It's a bit outdated, but with some modifications it's working fine. In case I see a request of interest for it here I could update it. Let me know.
After adding postfix and changing port number for ssh and a couple of other tweaks it's just the way I want it. Lovely.