---
layout: post
title: "Maven bash-completion entry on Gentoo"
description: ""
category: programming
tags: scala
---
{% include JB/setup %}

Put the simple file in `/usr/share/bash-completion` with the ones I use most.

    #!/bin/sh
    _m2_make_goals()
    {
    plugin=$1
    mojos=$2
    for mojo in $mojos
    do
    export goals="$goals $plugin:$mojo"
    done
    }
    _m2_complete()
    {
    local cur goals
    COMPREPLY=()
    cur=${COMP_WORDS[COMP_CWORD]}
    goals='clean compile test install package deploy site'
    goals=$goals _m2_make_goals "eclipse" "eclipse"
    goals=$goals _m2_make_goals "eclipse" "clean"
    goals=$goals _m2_make_goals "dependency" "tree"
    goals=$goals _m2_make_goals "dependency" "list"
    cur=`echo $cur | sed 's/\\\\//g'`
    COMPREPLY=($(compgen -W "${goals}" ${cur} | sed 's/\\\\//g') )
    }
    complete -F _m2_complete -o filenames mvn

And then the ``eselect bashcomp enable <filename>`` Will be overwritten the next time the gentoo ebuild for bashcomp is updated or reinstalled.

{% include share.html %}
