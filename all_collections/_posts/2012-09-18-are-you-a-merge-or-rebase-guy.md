---
layout: post
title: Are you a merge or rebase guy?
date: 2012-09-18
tag: Git,Version-control
description: I know, by now you read almost every tutorial about how to get started with git. You know how to create your repo, add stuff to it and push to
author: Marco Monteiro
categories: [Git,Version-control]
---

I know, by now you read almost every tutorial about how to get started with git. You know how to create your repo, add stuff to it and push to your remote. You started branching and everything is now great. Then you read the term Rebase somewhere and think - who wants that? I have Merge. 

Well today we talk about the differences between them. Also have in mind that these concepts can be applied to both Git and Mercurial.
Merge or Rebase?
<!--more-->

> As you're no doubt aware, Git and Mercurial are great at re-integrating divergent lines of development through merging. They have to be, since their design strongly encourages developers to commit changes in parallel in their own distributed environments. Eventually some or all of these commits have to be brought together into a shared graph, and merging and rebasing are two primary ways that let us do that. So which one do you use?

> in: sourcetreeapp.com

Ok let’s start be defining both.

**Merge**

Join two or more development histories together.

Incorporates changes from the named commits (since the time their histories diverged from the current branch) into the current branch. This command is used by git pull to incorporate changes from another repository and can be used by hand to merge changes from one branch into another.

Assume the following history exists and the current branch is “master”: 

	  A---B---C topic
	 /
    D---E---F---G master

Then "git merge topic" will replay the changes made on the topic branch since it diverged from master (i.e., E) until its current commit (C) on top of master, and record the result in a new commit along with the names of the two parent commits and a log message from the user describing the changes.

**Rebase**

Forward-port local commits to the updated upstream head.

Assume the following history exists and the current branch is “topic”:

          A---B---C topic
         /
    D---E---F---G master

From this point, the result of either of the following commands:

    git rebase master
    git rebase master topic

Would be:

                  A'--B'--C' topic
                 /
    D---E---F---G master

If the upstream branch already contains a change you have made (e.g., because you mailed a patch which was applied upstream), then that commit will be skipped. For example, running git rebase master on the following history (in which A’ and A introduce the same set of changes, but have different committer information):

          A---B---C topic
         /
    D---E---A'---F master

will result in:

                   B'---C' topic
                  /
    D---E---A'---F master

And it can get more and more complex than this. But trying to resume what it is to a more simple definition in contrast to Branching.

Rebasing unifies the lines of development by re-writing changes from the source branch so that they appear as children of the destination branch effectively pretending that those commits were written on top of the destination branch all along. 

**Pros and cons**

**Merging Pros**

* Simple to use and understand.
* Maintains the original context of the source branch.
* The commits on the source branch remain separate from other branch commits, provided you don't perform a fast-forward merge. This separation can be useful in the case of feature branches (remember git-flow?), where you might want to take a feature and merge it into another branch later.
* Existing commits on the source branch are unchanged and remain valid; it doesn't matter if they've been shared with others.

**Merging Cons**

If the need to merge arises simply because multiple people are working on the same branch in parallel, the merges don't serve any useful historic purpose and create clutter.
Rebase Pros

Simplifies your history.
Is the most intuitive and clutter-free way to combine commits from multiple developers in a shared branch
Rebase Cons

Slightly more complex, especially under conflict conditions. Each commit is rebased in order, and a conflict will interrupt the process of rebasing multiple commits. With a conflict, you have to resolve the conflict in order to continue the rebase. SourceTree guides you through this process, but it can still become a bit more complicated.
Rewriting of history has ramifications if you've previously pushed those commits elsewhere. In Mercurial, you simply cannot push commits that you later intend to rebase, because anyone pulling from the remote will get them. In Git, you may push commits you may want to rebase later (as a backup) but only if it's to a remote branch that only you use. If anyone else checks out that branch and you later rebase it, it's going to get very confusing.
You decide which one to use and where. It’s up to you, personally I rarely use rebase.

Article based on the gitbook.