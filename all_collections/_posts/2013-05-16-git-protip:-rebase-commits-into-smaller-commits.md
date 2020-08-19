---
layout: post
title: Git ProTip Rebase Commits into smaller commits
date: 2013-05-16
tag: Git,merge,Versioncontrol
description: Yeah, thats right. If youre like me you have a small compulsion to commit every small task you complete
author: Marco Monteiro
categories: [Git,merge,Versioncontrol]
---

Yeah, that's right. If you're like me you have a small compulsion to commit every small task you complete. In some cases that can be a good practice. However, when you're working with a large team, or even on a open source project that has lot's of contributors that can be a PITA in the long run. Imagine you're looking for all the changes done while creating a feature, and your history is full of small commits. Finding what you're looking for is not going to be easy.

<!--more-->

So I started digging a way so I can continue on my normal commit rate, but before I push things into my remote(s) I can decide if my code will go divide into all of those commits or if I want to ...merge“ them into a single commit.

Let's look at the rebase command and if you'll see that is one called —interactive. Apparently the most common use for this one is to squash commits. What I mean by that is that you can pick up all your commits and combine them into larger ones.

	-i, --interactive Let the user edit the list of commits to rebase

A word of caution: Only do this on commits that haven't been pushed an external repository. If others have based work off of the commits that you're going to delete, plenty of conflicts can occur. Just don't rewrite your history if it's been shared with others.