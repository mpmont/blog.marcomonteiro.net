---
layout: post
title: Updating your Codeigniter installation with git
date: 2012-08-21
tag: codeigniter,Git,Version-control
description: Ever since Codeigniter moved from Bitbucket to Github I craved for one easy way to update my applications every time a new version gets out. Turns out there is none.
author: Marco Monteiro
categories: [codeigniter,Git,Version-control]
---

Ever since Codeigniter moved from Bitbucket to Github I craved for one easy way to update my applications every time a new version gets out. Turns out there is none. And as you can see here, the updating process is always kinda boring specially if a major version is out. Since the version 3.0 is around the block I’m going to show you how I normally upgrade my codeigniter applications.
<!--more-->
First things first, I’m assuming that you work with git in your normal day to day workflow. If you don’t use it, or even worst don’t know how to use it, stop reading this and without further delay go learn how to use it. (You can check this link for that!).

Ok, so now that you can’t live without using git let’s start this thing. 

1. Visit the codeigniter official repository on github.
2. Add that repository as another remote in your project.

For that navigate to the root of your project in your terminal and do this:

        $ git remote add codeigniter git://github.com/EllisLab/CodeIgniter.git
		
Now if you list all your remotes you should get the following result:

		$ git remote
		codeigniter
	 	origin

Now that you have codeigniter as a remote you have access to all branches that are contained within that repository. 

3. Before you continue make sure that your project is safe and create a new branch from your develop branch (assuming you’re using git flow) let’s call it feature/codeigniter_upgrade. 

4. Now that you have your brand new branch created and that your project is safe the only thing that you have to do is look at all the codeigniter branches and find the latest codeigniter stable branch.

At the moment you’ll be looking for 2.1-stable or hopefully when you read this you’ll be looking for 3.0-stable. Let’s hope that’s the case. (I’m using Source Tree so you can have a more visual context of what’s going on.)

Moving on. 

5. Now that you found the branch you want to merge you just need to check out to that branch. For that you just need to do:

		$ git branch 2.1-stable codeigniter/2.1-stable
		
And like that now you have a local copy of the latest stable version of codeigniter in your local repository.

6. Now the only thing left to do is to merge your new 2.1-stable branch into your feature/codeigniter_upgrade. 

7. After the merge there will be some things to consider, since you’ll obviously get some merge conflicts. 

**List of possible conflicts: **

* application/config.php
* application/routes.php
* application/database.php
* application/contants.php
* index.php
* user_guide (if you sill have one in your root)

All these conflicts are actually quite easy to resolve, since normally you just need to pick your version over the original one. (Just make sure none of these file have any major changes in the new codeigniter version).

I know this is far from a straight forward solution, but it’s better than changing file by file and probably forget something in the process. Sure it’ll take some time, and it can give you some headaches on the final part of the process, but if you have some experience with git just go for it, you can’t lose anything. Because you know, if you work with git, you never really lose anything. 

Have fun.