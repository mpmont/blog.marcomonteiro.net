---
layout: post
title: How to clean up your environment when using docker
date: 2019-03-10
tag: 2019,docker,linux,Webdev
description: After a few projects we all know that you can have a real mess on your rig. Specially when it comes to saving space. So how to do that?
author: Marco Monteiro
categories: [2019,docker,linux,Webdev]
---

After a few projects we all know that you can have a real mess on your rig. Specially when it comes to saving space. So how to do that?

<!--more-->

For this purpose you can use following command:

	$ docker system prune -a

This will give you the following output:

	WARNING! This will remove:
			- all stopped containers
			- all networks not used by at least one container
			- all images without at least one container associated to them
			- all build cache
	Are you sure you want to continue? [y/N]

You can be even a bit more hardcore and shove a **-a** command in there, that will remove everything, not just the images.

If your purpose is just to force Docker to rebuild images without using cache then use following combination:

	$ docker system prune
	$ docker-compose build --no-cache

Then run up command as usual:

	$ docker-compose up

Stay clean!