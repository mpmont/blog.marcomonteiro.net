---
layout: post
title: Getting started with vagrant
date: 2014-01-04
tag: development,environment,vagrant,Webdev
description: Recently I wrote a post about my dev setup. However someone has been recommending me for a while to start using Vagrant. But I never did.
author: Marco Monteiro
categories: [development,environment,vagrant,Webdev]
---

Recently I wrote a post about [my dev setup on mac](http://blog.marcomonteiro.net/post/my-dev-setup-on-mac). However someone has been recommending me for a while to start using Vagrant. But I never did. Specially because my dev setup was working fine.

A few days ago, I decided it was time to do a clean install on my mac, and start fresh. That means it's time for some experimenting.

<!--more-->

**What is Vagrant?**

>Vagrant is a tool for building complete development environments. With an easy-to-use workflow and focus on automation, Vagrant lowers development environment setup time, increases development/production parity, and makes the "works on my machine" excuse a relic of the past.

>Vagrant was started in January 2010 by Mitchell Hashimoto. For almost three years, Vagrant was a side-project for Mitchell, a project that he worked on in his free hours after his full time job. During this time, Vagrant grew to be trusted and used by a range of individuals to entire development teams in large companies.

I look at this and I see two features that interest me. First I'll be developing on a virtual machine that is equal to the one I'll be deploying in the future. Then, since every configuration, dirty hack or whatever will be done on that virtual machine. My computer will stay clean of all the experimenting a the web developer life requires.

I work mainly with PHP, so the best way to start with Vagrant is to use something like [puphpet](https://puphpet.com/).

Puphpet is a simple GUI to set up virtual machines for PHP Web development. In a few simple steps you'll have your Manifest ready to start working with Vagrant.

First you setup the deploy target. In this case it will be local. You choose what kind of virtual machine you need and you give it a name and IP address. Then you setup what path will be synced with the VM.

After that is pretty straight forward. You just have to configure some of the aspects of your VM that are specific to you dev environment. This includes: virtual hosts, php version, composer, PEAR modules, PECL Modules, XDebug. All your database preferences, database names, users and passwords. After that you're ready to go.

Before you do anything with the files you just downloaded you need to download VirtualBox and install it. After that the process is quite simple.

All you need to do is open your terminal. Navigate to your downloaded files from Puphpet and run the following command:

	$ vagrant up

This will install and start the virtual machine you ended up choosing. After that, you can access your server with the IP you used during the Puphpet setup process or you can configure the virtual host.

Here's a list of the available commands to use Vagrant.

* <i class="icon-angle-right"></i> **box** - manages boxes: installation, removal, etc.
* <i class="icon-angle-right"></i> **destroy** -stops and deletes all traces of the vagrant machine
* <i class="icon-angle-right"></i> **halt** - stops the vagrant machine
* <i class="icon-angle-right"></i> **help** - shows the help for a subcommand
* <i class="icon-angle-right"></i> **init** - initializes a new Vagrant environment by creating a Vagrantfile
* <i class="icon-angle-right"></i> **package** - packages a running vagrant environment into a box
* <i class="icon-angle-right"></i> **plugin** - manages plugins: install, uninstall, update, etc.
* <i class="icon-angle-right"></i> **provision** - provisions the vagrant machine
* <i class="icon-angle-right"></i> **reload** - restarts vagrant machine, loads new Vagrantfile configuration
* <i class="icon-angle-right"></i> **resume** - resume a suspended vagrant machine
* <i class="icon-angle-right"></i> **ssh** - connects to machine via SSH
* <i class="icon-angle-right"></i> **ssh-config** - outputs OpenSSH valid configuration to connect to the machine
* <i class="icon-angle-right"></i> **status** - outputs status of the vagrant machine
* <i class="icon-angle-right"></i> **suspend** - suspends the machine
* <i class="icon-angle-right"></i> **up** - starts and provisions the vagrant environment

That's it. Easy like that.