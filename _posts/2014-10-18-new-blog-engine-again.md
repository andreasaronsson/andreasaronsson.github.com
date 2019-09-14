---
layout: post
title: "New blog engine again."
description: ""
category: general
tags: [blog]
---
{% include JB/setup %}

This time it is [Jekyll](http://jekyllrb.com/) from [Jekyllbootstrap](http://jekyllbootstrap.com/) on [Github](https://github.com)
to which I have moved almost all of my private stuff now.
Both wonderful and works more or less exactly as one would want.
To create
a new post it is as simple as

{% highlight bash %}
rake post title="New blog engine again"
{% endhighlight %}

and then edit the created file with emacs in markdown-mode.
When done I call

{% highlight bash %}
git add.;git commit -m"Update site";git push
{% endhighlight %}

which I've created an alias for.
Very easy and fits my writing habits perfectly.

Ack. Just noticed the preformatted blocks are no good to copy paste from.
I guess I can just use the code blocks without syntax highlighting.

Generating a preview is as easy as 

{% highlight bash %}
jekyll serve
{% endhighlight %}


{% include share.html %}
