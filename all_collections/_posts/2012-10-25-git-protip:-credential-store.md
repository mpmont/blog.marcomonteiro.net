---
layout: post
title: Git protip: credential-store
date: 2012-10-25
tag: Git,Version-control
description: Only a few days ago I found out about this feature. I was always typing my credentials every-time I wanted to push to a remote. Well, no more! With git-credential-store
author: Marco Monteiro
categories: [Git,Version-control]
---

Only a few days ago I found out about this feature. I was always typing my credentials every-time I wanted to push to a remote. Well, no more! With git-credential-store - Helper you can store credentials on disk.
<!--more-->
		$ git config credential.helper 'store [options]'

Using this helper will store your passwords unencrypted on disk, protected only by filesystem permissions. If this is not an acceptable security tradeoff there’s always git-credential-cache.

**git-credential-cache**

		$ git config credential.helper 'cache [options]'

This command caches credentials in memory for use by future git programs. The stored credentials never touch the disk, and are forgotten after a configurable timeout. The cache is accessible over a Unix domain socket, restricted to the current user by filesystem permissions.

There you go!