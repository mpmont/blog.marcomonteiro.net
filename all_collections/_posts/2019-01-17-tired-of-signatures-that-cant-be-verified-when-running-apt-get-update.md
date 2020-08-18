---
layout: post
title: Tired of signatures that can't be verified when running apt-get update?
date: 2019-01-17
tag: 2019,apt-get,linux,ppa,snap
description: If everytime you run sudo apt-get update you get the following error Err 14 URL HERE The following signatures couldnt be verified because the public key is not available
author: Marco Monteiro
categories: [2019,apt-get,linux,ppa,snap]
---

If everytime you run *sudo apt-get update*   you get the following error "Err:14 URL HERE The following signatures couldn't be verified because the public key is not available: NO_PUBKEY PUBLIC_KEY_HERE" and like me you want to fix that. Don't worry, I got your back.

<!--more-->

I got this error with the ppa related to the vivaldi browser, so my error was like this:

	Err:14 http://repo.vivaldi.com/stable/deb stable Release.gpg The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D04CE49EFB20B23

The fix

By far the simplest way to handle this now is with Y-PPA-Manager (which now integrates the launchpad-getkeys script with a graphical interface).

To install it, first add the webupd8 repository for this program:

	$ sudo add-apt-repository ppa:webupd8team/y-ppa-manager

Update your software list and install Y-PPA-Manager:

	$ sudo apt-get update
	$ sudo apt-get install y-ppa-manager

Run y-ppa-manager (i.e. type y-ppa-manager then press enter key).

When the main y-ppa-manager window appears, click on "Advanced."

From the list of advanced tasks, select "Try to import all missing GPG keys" and click OK.

You're done! As the warning dialog says when you start the operation, it may take quite a while (about 30 seconds for me) depending on how many PPA's you have and the speed of your connection.


