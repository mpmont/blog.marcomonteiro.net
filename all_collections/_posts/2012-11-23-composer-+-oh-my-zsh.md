---
layout: post
title: Composer + Oh-My-Zsh
date: 2012-11-23
tag: composer,my-zsh,php,zsh
description: Oh-my-zsh is a community driven framework that you can use to manage your zsh configuration. 

**What about composer?**
I have a blog you know? I write stuff from time to
author: Marco Monteiro
categories: [composer,my-zsh,php,zsh]
---

Oh-my-zsh is a community driven framework that you can use to manage your zsh configuration. 

**What about composer?**
I have a blog you know? I write stuff from time to time. Keep up, Internet. 

<!--more-->

**The plugin!**
This plugin is quite simple actually. It gives you auto-complete and a bunch of useful aliases:

		c = 'composer'
		c  for autcomplete
		csu = 'composer self-update'
		cu = 'composer update'
		ci = 'composer install'
		ccp = 'composer create-project'
		cget = installs composer on the current path

If you’re looking for the composer commands you can see those [here](http://getcomposer.org/doc/03-cli.md).

To add the plugin just make sure you’re running the latest version of oh-my-zsh then edit your .zshrc file and add the composer plugin to the list of your active plugins.

There, done! 