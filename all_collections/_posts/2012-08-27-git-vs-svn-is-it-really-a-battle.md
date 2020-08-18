---
layout: post
title: Git vs Svn is it really a battle?
date: 2012-08-27
tag: Git,Version-control
description: Since I wrote that last post on how to update your codeigniter installation with git, I got a question on why use git? (at least this time was why use
author: Marco Monteiro
categories: [Git,Version-control]
---

Since I wrote that last post on how to update your codeigniter installation with git, I got a question on why use git? (at least this time was why use git, and not why use any kind of version control). 
<!--more-->
Normally I post some of my posts on Forrst, and there was the place the question took place. Take a look:

> Marco,
> 
> really interesting. We use Codeigniter for our applications. May sound so noob but... Should we always be up to date? It's secure to update?
> 
> I'm one of those that doesn't use git. We have our own SNV and I can't still find what is what you guys see in git to not be able to live without it. Can you give a bit of details? :-)

So I promised the dude I would blog about this, since the freaking text-area where you comment on Forrst is so damn small.

I’ve made some research about this and obviously I’m not the 1st one blogging about this, so I decided to quote some stuff.

If you have compelling requirements for a single, certain, master copy of your work, use Subversion. You can do this with Git, so long as there are no slip-ups. But you can't do anything else with Subversion (slip-ups or no), and ...compelling requirements“ like Sarbanes-Oxley are happier with guarantees than possibilities.
If you plan to maintain parallel, largely shared but permanently somewhat different lines of the same product, use Git. One common example: perhaps you have a large product that you customize for each customer. The customizations are permanent, and generally not shared among code lines, but most of the code is common to all. Git was designed for just this case (in Git terms, local customizations to the common core, and occasional feature or bug-fix contributions back up-tree).
Neither of those? Take your pick, you should be fine with either tool.
in: blog.collab.net

No need to clarify this. Let’s do a quick run on the best points of both.

Git’s Major Features Over Subversion

Distributed Nature (Git was designed from the ground up as a distributed version control system. Being a distributed version control system means that multiple redundant repositories and branching are first class concepts of the tool.)
Access Control (Due to being distributed, you inherently do not have to give commit access to other people in order for them to use the versioning features. Instead, you decide when to merge what from whom.)
Branch Handling (Branches in Git are a core concept used everyday by every user. In Subversion they are more cumbersome and often used sparingly.)
Performance (Git is extremely fast. Since all operations except for push and fetch are local there is no network latency involved)
Smaller Space Requirements (Git’s repository and working directory sizes are extremely small when compared to SVN.)
Obviously there’s some nice things about SVN too. Let’s see.

Subversion’s Major Features Over Git

User Interfaces Maturity (Currently Subversion has a wider range of user interface tools than Git. For example there are SVN plugins available for most popular IDEs. There is a Windows Explorer shell extension. There are a number of native Windows and Mac OS X GUI tools available in ready-to-install packages.)
Single Repository (Since Subversion only supports a single repository there is little doubt about where something is stored. Once a user knows the repository URL they can reasonably assume that all materials and all branches related to that project are always available at that location.)
Access Controls (Since Subversion has a single central repository it is possible to specify read and write access controls in a single location and have them be enforced across the entire project.)
So as you can see they both have their ups and downs. For me I still think Git is way better than SVN. I find it more intuitive/natural to use.

This article does not aspire to be final proof of anything, it’s just a collection of stuff I found on the web. Hell, if someone reads this and is not using any kind of version control and starts using it because of it I say - Mission accomplished. 

Take some time to watch this talk from the great Linus Torvalds about Git. If I can’t convince you about using git he’s the man to do it.

<iframe width="600" height="450" src="//www.youtube.com/embed/4XpnKHJAok8" frameborder="0" allowfullscreen></iframe>