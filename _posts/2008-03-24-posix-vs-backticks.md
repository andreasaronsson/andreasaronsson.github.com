---
layout: post
title: "POSIX vs backticks"
---

================

A couple of years ago, I was sifting through the <a target="_blank" href="http://linux.die.net/man/1/bash">manpage for bash.</a> I was at the time looking for something else, but my attention was caught by the section about <b>command substitution</b>, I. E. the art of letting a command be substituted by the output of it's execution. In shells, there are two ways in which this can be accomplished; backticks /backquotes or braces. When I read it, it said backticks were <b>old</b> style. I searched for a bit and found a reference that it was deprecated. <a href="http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.baseadmn/doc/baseadmndita/korn_shell_comm_sub.htm">More info here</a> that states that POSIX and OPG4 recommends braces for portability. This time, I thought nothing more of it feeling assured that with braces, all would be well, I would be safe and so would my friends, brothers, sisters and parents. Naturally, I started preaching about it more or less in the same manner as do I on so much else like operating systems and so forth. Also I used braces exclusively in all my scripts. Naturally.

Braces has some advantages. You do not have to escape them when you nest commands, backslashes are literal all the time (inside backticks they have special meaning (escaping) when preceding $, ' and \) and there's some situations with undefined results using unescaped backticks inside comments. In the light of these facts, one might think that I was a do-good'er of some dignity preaching to the uneducated masses. Because, a crushing majority of the people I have discussed with have been ingorant about anything else but backticks. When I've brought up braces they mostly go: Oh? Braces, you say? Neer heard of. The last individual that reacted like this had a bit more to share than a raised eyebrow. It turns out that on older machines, like solaris 8, the <b>sh</b> implementation does not use braces. There goes portability.

The <a href="http://www.unix.org/single_unix_specification/">bible</a> as I would have thought of it apparantly has some shortcomings. 
Now I have to ponder my weapon of choice for command substitution. As it wasn't enough with eclipse vs netbeans stalemate.