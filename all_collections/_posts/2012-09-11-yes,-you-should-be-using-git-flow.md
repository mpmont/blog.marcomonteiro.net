---
layout: post
title: Yes, you should be using git-flow
date: 2012-09-11
tag: flow,Git,Version-control
description: I’ve been talking a lot about git these days, and I still have a few articles to do about it. With that in mind today I’m here to talk to
author: Marco Monteiro
categories: [flow,Git,Version-control]
---

I’ve been talking a lot about git these days, and I still have a few articles to do about it. With that in mind today I’m here to talk to you a bit about git-flow.

Once again, I’m not here to re-invent the wheel. If someone has good articles about something I’m going to point you there during this process.
<!--more-->

**What is git-flow?**

In early 2010, Vincent Driessen wrote an article called ...A successful Git branching model“ which recommended an approach called git-flow to use git branches in your development cycle. The idea was to standardise branching and merging when developing features, handling releases and managing hot fixes, in order to be consistent and gain the advantages of git's 'branchy' development model. Using many separate branches in Git gives you lots of flexibility, but it can get complex. Adopting a standardised approach has many advantages:

> * Keep your repository tidier
> * Keep your procedures clearer
> * Move between projects more easily with familiar branch structures
> * Get new developers up to speed more quickly
>
> in: sourcetreeapp.com

**Summary of the concept**

Development branch (usually called 'develop') This is your main development branch where all the changes destined for the next release are placed, either by directly committing small changes or by merging other branches (e.g. feature branches) into this branch.
Production branch (usually called 'master') This branch represents the latest released / deployed codebase. Only updated by merging other branches into it.

Feature branches (usually prefixed with 'feature/')When you start work on anything non-trivial, you create a feature branch. When finished, you'll merge this branch back into the development branch to queue it for the next release.
Release branches (usually prefixed with 'release/')When you're about to package a new release, you create a release branch from the development branch. You can commit to it during your preparation for a release, and when it's ready to be deployed, you merge it into both the development branch and the master branch (to indicate that the release has been deployed).
Hotfix branches (usually prefixed with 'hotfix/') If you need to patch the latest release without picking up new features from the development branch, you can create a hotfix branch from the latest deployed code in master. Once you've made your changes, the hotfix branch is then merged back into both the master branch (to update the released version) and the development branch (to make sure the fixes go into the next release too)

**How to use git-flow?**

After installing git-flow, you can start a new repository in the current directory or convert an existing one to the new branch structure:

		$ git flow init

It will ask you a bunch of questions, but you probably want to accept the default values:

	No branches exist yet. Base branches must be created now.
 		Branch name for production releases: [master]
 		Branch name for "next release" development: [develop]
 		How to name your supporting branch prefixes?
 		Feature branches? [feature/]
 		Release branches? [release/]
	 	Hotfix branches? [hotfix/]
 		Support branches? [support/]
 		Version tag prefix? []

Now, simply use Git like you're used to, but only work on some small features in the develop branch. If you need to work on a bigger feature, just create a feature branch based on develop. Let's say you want to add a login page:

		$ git flow feature start login

This will create a new branch called feature/login, based on our develop branch and switches to it. Commit away and after you finish working on the login page, simply finish it:

		$ git flow feature finish login

It'll merge feature/login back to develop and delete the feature branch.

When you're feature complete, simply start a release branch â€” again, based on develop â€” to bump the version number and fix the last bugs before releasing:

		$ git flow release start v0.1.0

When you finish a release branch, it'll merge your changes to master and back to develop, so you don't have to worry about your master being ahead of develop.

The last thing that makes git-flow awesome is it's ability to handle hotfixes. You start and finish a hotfix branch like anything else, but it's based on master so you can quickly fix it when something's broken production and merge it back to master and develop using finish.

*Tutorial by: Jeff Kreeftmeijer*

This article is basically a roundup. Because I found there was none “small” article that shows both the theory behind git-flow and the actual use of it.

For a more information about this check this [article](http://yakiloo.com/getting-started-git-flow/).

Also, if you don’t want to use git-flow per say, at least use the branching logic behind it.