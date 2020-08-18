---
layout: post
title: Are you still using NFS to sync your file over to your virtual box?
date: 2017-01-19
tag: box,development,vagrant
description: For quite a while I must admit I been using this method to sync my files. This has been problematic, files not really syncing in real time can be a
author: Marco Monteiro
categories: [box,development,vagrant]
---

For quite a while I must admit I been using this method to sync my files. This has been problematic, files not really syncing in real time can be a pain in the ass, sepecially when you're making changes on front-end and want to see those changes on the fly.

So, do yourself a favor and change to rsync. To do so, you just need to edit your vagrant file for something like this:

    config.vm.synced_folder "./", "/vagrant", type: "rsync",
        rsync__exclude: ".git/"

This way you're using rsync and you're excluding your git folder. You can add other folder there. Now, when you start your vagrant box you have to do this:

    $ vagrant up
	$ vagrant rsync-auto

And your files will be synced automatically.