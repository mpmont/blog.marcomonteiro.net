---
layout: post
title: Linux not reading the /etc/hosts file
date: 2021-12-21
tag: linux, webdev, manjaro, arch
description: In one of my distros last update my hosts file was not being interpreted anymore
author: Marco Monteiro
categories: [ linux, webdev, manjaro, arch ]
---
This week I restarted my laptop. That does not happen too often. Mostly when I let the batery run out for some reason. So when I got back into the system I ran into a weird one. My /etc/hosts file was not being read.

<!--more-->

Let's say I did:

    $ ping localhost

Everything was working out as it should. However I had quite a few more host rules there. like

    127.0.0.1    foo.loc

However when I tried to ping foo.loc it was not working at all. Tried to flush my DNS cache and nothing was working. Then I ran into a post on stackoverflow that did the following solution was to edit /etc/nsswitch.conf file (you may use command sudo vim /etc/nsswitch.conf). I've changed line:

    hosts:          files mdns4_minimal [NOTFOUND=return] dns

to:

    hosts:          dns files mdns4_minimal [NOTFOUND=return]

and now it is working as expected!

I hope this helps anyone that comes accross the same problem.

