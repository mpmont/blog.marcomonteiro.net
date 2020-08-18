---
layout: post
title: git refusing to merge unrelated histories
date: 2019-03-12
tag: 2019,Git,git-flow,Version-control
description: One of the things that happens to me a lot is when I start a new project on my computer that someone else started on our main repo  is this
author: Marco Monteiro
categories: [2019,Git,git-flow,Version-control]
---

One of the things that happens to me a lot is when I start a new project on my computer that someone else started on our main repo  is this error saying that I'm trying to merge unrelated histories.

This happens mostly because someone on the other side already started the master and develop branch and made some commits to it.

<!--more-->

However what I normally do is:

	$ git init
	$ git flow init
	$ git remote add origin [insert url here]
	$ git pull origin develop

This is when everything turns to shit and I get the following output:

	$ fatal: refusing to merge unrelated histories
	$ Error redoing merge 1234deadbeef1234deadbeef

However this is quite easy to solve. All you have to do is shove a *--allow-unrelated-histories* into your pull command. Like so:

	$ git pull origin develop --allow-unrelated-histories

This will also work if you're trying to merge or rebase code.
