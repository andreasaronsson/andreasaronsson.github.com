---
layout: post
title: "Github and maven-release-plugin setup"
description: ""
category: programming
tags: github,maven,maven-release-plugin,maven-scm-plugin
---
{% include JB/setup %}

Assuming you have a [Github](http://github.com) account setup you can use the
[maven-release-plugin](http://maven.apache.org/maven-release/maven-release-plugin/) to push the changes associated with a release to
github. Further, assuming you have set up the github account with an ssh key you can configure the maven-release-plugin to push your
changes not requiring entering a password every time a release is created. It appears to be canon to use the term "cut a release"
for this activity. Eventually I'll get around to asking my english speaking friends about this. Anyway, this requires you to have an
`<scm>` element in your project description file. It must look like this:

  <scm>
    <connection>scm:git:git@github.com:username/projectname.git</connection>
    <developerConnection>scm:git:git@github.com:username/projectname.git</developerConnection>
    <url>https://github.com/username/projectname</url>
  </scm>

The data inside the elements is a colon separated (only the first two is significant for the plugin making up three partitions in
all). The first two parts; `scm` and `git` tells it to use the [maven-scm-plugin](https://maven.apache.org/scm/maven-scm-plugin/)
and its git executor. The rest is passed in as an argument. Now to the thing that made me spend a good amount of time before getting
this to work. There is some [debate](http://stackoverflow.com/questions/5948659/trailing-slash-in-urls-which-style-is-preferred) on
whether a "proper" URL shall end with a slash or not. I have been in the pro-add-slash camp and yesterday I came to regret it. It
turns out that adding a trailing slash to the `<developerConnection>` makes the invocation of `mvn release:prepare` fail complaining
about either missing repo or failure to authorize. The error messages led me to believe that I had constructed the data in error so
I tried using `ssh://` and slash instead of colon etc.

With hope this helps someone. 
