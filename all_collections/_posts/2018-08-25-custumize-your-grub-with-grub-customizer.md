---
layout: post
title: Custumize your grub with Grub Customizer
date: 2018-08-25
tag: 2018,grub,linux,ubuntu
description: For those who need to modify the default Grub boot-loader settings, Grub Customizer is a useful tool with a graphical user interface.
author: Marco Monteiro
categories: [2018,grub,linux,ubuntu]
---

For those who need to modify the default Grub boot-loader settings, [Grub Customizer](https://launchpad.net/grub-customizer) is a useful tool with a graphical user interface.

**Main features:**

> Move, remove or rename menuentries (they stey updatable by update-grub)

> Edit the contents of menuentries or create new ones (internally it edits the 40_custom)

> Support for GRUB2 and BURG

> Reinstallation of the bootloader to MBR

> Settings like default operating system, kernel params, background image and text colors etc.

> Changing the installed operating system by running on a live cd

**To install Grub Customizer in Ubuntu:**

The software has an official PPA repository contains the packages for all current Ubuntu releases.

1. Open terminal either via Ctrl+Alt+T or by searching for ‘terminal’ from app launcher. When it opens, run command to add the PPA:

        sudo add-apt-repository ppa:danielrichter2007/grub-customizer

2. After added the PPA, run commands one by one to refresh package cache and install Grub Customizer:

        sudo apt-get update
        sudo apt-get install grub-customizer

Once installed, launch the software from your application launcher and enjoy!
