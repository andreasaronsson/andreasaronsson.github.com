---
layout: post
title: "Doubleclick links in terminal"
category: sysadm
---
{% include JB/setup %}
{% include share.html %}

For a very long while now, several years actually, I've been a bit
annoyed by the behaviour of terminals under X when you doubleclick
links. What the UI considers a word is selected. Selection 'starts' at
the point that is doubleclicked and 'spreads' in each direction,
stopping at a char it considers to be a word delimiter. A space is
probably always considered a delimiter. Sometimes a '?' too, and often
',' as well. This has been very annoying for me as I spend quite alot
of time in irc (irssi in a screen, its lovely in combination with
bitlbee; icq, irc etcetc in the same screen.) and every now and then
someone pastes an url which I want to doubleclick and then paste into
my browser. Now the selection stops prematurely as it's not uncommon
for a hyperlink to contain one of the characters that is in the word
delimiter list. I've thought of this as a limitation to the system I
use and, although annoyed, never gave it much thought. Maybe I've been
to susceptible to propagandaists telling me gnu/linux is
user-unfriendly.

A couple of weeks ago I started to think a little about it and the
solution is rather simple. I use Eterm more or less exclusively.  In
``~/.Eterm/user.cfg`` I've put this:

    <eterm-0.9>
    begin misc
    cut_chars "\t\\\`\\\"\'() *,;<>[]{|}"
    end misc
    

This might not be perfect but it's certainly served it's purpose this
far as I have been able to doubleclick on the links and then
middleclick in the address field (or open a new tab) in the
browser. My OS is even better =)
