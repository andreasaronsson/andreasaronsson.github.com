---
layout: post
title: "Xorg config notes"
---

Just got myself a "SyncMaster 245B". Samsung FTW! This beauty is capable of 1920x1200 wide screen resolution. While I was at it, I switched from VGA to DVI cable too. While configuring I made some interesting notes; 
When X starts with the VGA cable, I have to put
<pre>
Option         "UseEDID" "FALSE"
Option         "UseEDIDFreqs" "FALSE"
Option         "UseEDIDDpi" "FALSE"
Option         "ModeValidation" "NoEdidModes"
</pre>

in the "Device" section of xorg.conf or else X (or maybe it's the nvidia driver, not sure perhaps someone knows?) won't bother at all with the "Modes" section you put in. This is because the hardware is probed for the EDID data which may (and will in this case) be read wrong when X starts. 

Also, I had to get a modeline to put in my "Monitor" section:
``/usr/bin/gtf 1920 1200 60`` Next, the DVI cable. (I have drilled a hole in the wall with my boxes in the closet so it's quite a fuzz changing cables =)). X starts. Blank screen. :-o
After I put <cite>forums.gentoo.org</cite> to work on my knowledge, I discovered that, contrary to my prior info that X doesn't distinguish between CRT and TFT, it actually vital that you have

    Option         "ConnectedMonitor" "DFP"

in your "Device" section. 

Now it's all good. (=</p>