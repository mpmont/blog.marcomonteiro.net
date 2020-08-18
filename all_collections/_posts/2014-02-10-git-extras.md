---
layout: post
title: Git extras
date: 2014-02-10
tag: alias,extras,Git,Version-control,workflow
description: I'm a heavy git user, hence I'm always trying to improve my workflow while using it. I normally have 3 ways of using git. I could use a gui client
author: Marco Monteiro
categories: [alias,extras,Git,Version-control,workflow]
---

I'm a heavy git user, hence I'm always trying to improve my workflow while using it. I normally have 3 ways of using git. I could use a gui client ([sourcetree](http://www.sourcetreeapp.com/)), normally I do this when I'm preparing a new release.

On my daily code day I would use git inside [Sublime Text 2](http://www.sublimetext.com/). That way I don't need to constantly change between my text editor of choice and a git gui or the terminal. However, from time to time, I use just the terminal. That happens for two reasons, one I could be using git remotely, or I could be doing something more difficult that couldn't be resolved inside sourcetree or [Sublime Text](http://www.sublimetext.com/).

<!--more-->

Yesterday I tried this new tool and I'm getting quite found of it. It's called Git Extras. You have 3 ways of getting it:

**Clone / Tarball:**

	$ make install

**One-liner:**

	$ (cd /tmp && git clone --depth 1 https://github.com/visionmedia/git-extras.git && cd git-extras && sudo make install)

**MacPorts**

	$ sudo port install git-extras

**Brew (buggy):**

	$ brew install git-extras

Here's a small screencast on how to use it.

<iframe src="//player.vimeo.com/video/45506445?color=ffffff" width="100%" height="350" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

This tool is specially useful when you're managing .gitignore files. Or when you want to know all the info about your repo. You just have to type git info and you'll get something like this:

	$ git info

    ## Remote URLs:

    origin              git@github.com:sampleAuthor/git-extras.git (fetch)
    origin              git@github.com:sampleAuthor/git-extras.git (push)

    ## Remote Branches:

    origin/HEAD -> origin/master
    origin/myBranch

    ## Local Branches:

    myBranch
    * master

    ## Most Recent Commit:

    commit e3952df2c172c6f3eb533d8d0b1a6c77250769a7
    Author: Sample Author <sampleAuthor@gmail.com>

    Added git-info command.

    Type 'git log' for more commits, or 'git show <commit id>' for full commit details.

    ## Configuration (.git/config):

    color.diff=auto
    color.status=auto
    color.branch=auto
    user.name=Sample Author
    user.email=sampleAuthor@gmail.com
    core.repositoryformatversion=0
    core.filemode=true
    core.bare=false
    core.logallrefupdates=true
    core.ignorecase=true
    remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
    remote.origin.url=git@github.com:mub/git-extras.git
    branch.master.remote=origin
    branch.master.merge=refs/heads/master

Awesome right?