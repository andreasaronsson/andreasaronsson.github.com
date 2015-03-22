---
layout: post
title: "Drupal upgrade"
category: sysadm
---
{% include JB/setup %}
{% include share.html %}

First post after upgrade =)
Just upgraded from 5.12 to 6.6
In short (NOTE! not a proper instruction just a debrief); 

 * put in offline mode
 * backup database and htdocs
 * emerge new version 
 * use 'updated' module to find the correct modules version for the new major version
 * uninstall as many contributed modules as possible
 * run webapp-config
 * copy back sites directory (.htaccess and robots.txt too if modified)
 * unpack the modules you want in the modules dir
 * run the www.yoursite.com/update.php
 * try to poke around as much as possible

There was some quirks, some of the modules I failed to uninstall wasn't working and I got some duplicate menu entries but apart from that I think it's ok. 
