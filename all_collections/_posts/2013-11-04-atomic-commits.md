---
layout: post
title: Atomic commits
date: 2013-11-04
tag: Git,tips,Version-control
description: I'm sure this happened to you before, more than one time actually. You have a big file, you changed lots of stuff in it, but those changes are not really
author: Marco Monteiro
categories: [Git,tips,Version-control]
---

I'm sure this happened to you before, more than one time actually. You have a big file, you changed lots of stuff in it, but those changes are not really related. One may be related to one class and the other to something completely different. Normally you should avoid that, your commits should *always* be specific to one task, feature or bug. If you do a small search about how to commit better you'll see that even the commit messages should have this notion.

<!--more-->

Your commit message should look something like this:

	Explain in one line what the commit is about (Issue number if possible)

	Describe the problem the commit solves.
	Justify why you chose the particular solution.
	Reference the issue number if not addressed in the title.

So if you're solving a bunch of problems in the same commit, your commit messages will tend to go off-road.

Ideally you want to separate those changes into different commits and there's only one way (that I know of) to do that.

Let's look at the git add command:

	git add [-n] [-v] [--force | -f] [--interactive | -i] [--patch | -p]
	[--edit | -e] [--[no-]all | --[no-]ignore-removal | [--update | -u]]
	[--intent-to-add | -N] [--refresh] [--ignore-errors] [--ignore-missing][--] [<pathspec>...]

The one we're looking for is ***git add -p***

>-p
--patch
Interactively choose hunks of patch between the index and the work tree and add them to the index. This gives the user a chance to review the difference before adding modified contents to the index.
This effectively runs add --interactive, but bypasses the initial command menu and directly jumps to the patch subcommand. See “Interactive mode” for details.

The ***-p*** flag is not only available for ***git add*** but also for ***git checkout*** (I haven't used this one yet).

>This means that you can use git checkout -p to selectively discard edits from your current working tree. See the “Interactive Mode” section of git-add(1) to learn how to operate the --patch mode.

Personally I have used the ***git add -p*** flag without even know about it when using a Git GUI. But sometimes you just need to go old school and use the terminal.

<i class="icon-external-link"></i> [Git add reference](http://git-scm.com/docs/git-add)

<i class="icon-external-link"></i> [Git checkout reference](http://git-scm.com/docs/git-checkout)