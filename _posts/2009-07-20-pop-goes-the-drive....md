---
layout: post
title: "Pop goes the drive..."
---

For about a year now I have had a very annoying problem with my file server. One of the two Seagate drives simply disappeared from time to time. It was never the same one and I couldn't tell what pattern the disappearances followed. The system log looked something like:

<pre>
Jul 11 18:55:02 hostname ata5.00: exception Emask 0x10 SAct 0x1 SErr 0x190002 action 0xe frozen
Jul 11 18:55:02 hostname ata5.00: edma_err_cause=00000020 pp_flags=00000003, SError=00180000
Jul 11 18:55:02 hostname ata5: SError: { RecovComm PHYRdyChg 10B8B Dispar }
Jul 11 18:55:02 hostname ata5.00: cmd 61/80:00:a9:47:55/00:00:1b:00:00/40 tag 0 ncq 65536 out
Jul 11 18:55:02 hostname res 40/00:00:a9:47:55/00:00:1b:00:00/40 Emask 0x10 (ATA bus error
</pre>

At first I assumed that it was due to a faulty SATA controller on my motherboard. I found a PCI-e card that I could fit into my motherboard. It seemed to work just fine for a while, apart from the hassle with motherboard not being able to boot directly from it and being forced to use a noisy old IDE drive for storing grub and kernel to boot from.
After a month or so, one of the hard drives popped out again. Dang. This time I started trying to diagnose my Seagate discs. They have excellent diagnostic tools that runs under linux on their <a href="http://www.seagate.com">website</a>. I even sent two of them back to seagate and got them refurbished. 
After a couple of months or so again it was time to resync the RAID due to discs popping out. Man, I was frustrated with this by now. Since the only things left was cabling and PSU by now and I found <a href="http://marc.info/?l=linux-ide&m=121519742526938&w=2">this</a>. I decided to go for a new PSU,  I ripped out the old FSP and put in a new <a href="http://www.corsair.com/products/vx/default.aspx">Corsair</a>. Corsair really has become my favourite ones over time. 
According to the info I found this problem should reappear during load. Since I've done a resync of the raid, have a couple of full backup jobs run and a bunch of my pictures uploaded to it, it really seems rock stable now =). 