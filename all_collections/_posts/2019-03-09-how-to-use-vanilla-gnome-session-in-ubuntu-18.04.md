---
layout: post
title: How to use vanilla gnome session in Ubuntu 18.04
date: 2019-03-09
tag: 2019,desktop environment,gnome,linux,ubuntu
description: Gnome if basically my favourite desktop environment, since I moved away from Mac OS and started using Linux full time I tried a lot of flavours. But always ended up
author: Marco Monteiro
categories: [2019,desktop environment,gnome,linux,ubuntu]
---

Gnome if basically my favourite desktop environment, since I moved away from Mac OS and started using Linux full time I tried a lot of flavours. But always ended up back into gnome.

However, I never really liked the Ubuntu implementation of it. I always preffer the vanilla version. But Ubuntu its still my favourite distribution so how to get both?

To get that vanilla gnome experience, open a terminal and enter the following line:

    $ sudo snap remove gnome-3-26-1604 gnome-calculator gnome-characters gnome-logs gnome-system-monitor

You'll be asked for your password and after the process is complete you should run the following:

    $ sudo apt install gnome-session

After this step you want to reboot your system. Then at the login screen, click on the small gear icon and select "Gnome on Xorg" to get to the vanilla session.

After that you need to run the following:

	$ sudo apt install vanilla-gnome-desktop vanilla-gnome-default-settings

This might take a while, but after all these packages are installed you need to reboot once more.

Once you login you're now in the default gnome session.