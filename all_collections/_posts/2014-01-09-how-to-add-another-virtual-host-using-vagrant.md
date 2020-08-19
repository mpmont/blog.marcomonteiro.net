---
layout: post
title: How to add another virtual host using Vagrant
date: 2014-01-09
tag: development,server,vagrant
description: Theres a lot of ways to use Vagrant. Some people create a virtual machine per project. I don't like that idea. I think it's best to create a virtual machine
author: Marco Monteiro
categories: [development,server,vagrant]
---

There's a lot of ways to use Vagrant. Some people create a virtual machine per project. I don't like that idea. I think it's best to create a virtual machine for each different server you have to deploy. So if I have 2 projects that are going to be deployed to the same server why should I create two virtual machines? Makes no sense to me. Those two projects belong in the same virtual machine.

<!--more-->

In any case, I hope I'm not the only one trying to do that. If I am, then I must be wrong and you should stop reading this post. Anyway. If you want to do that, you have to create more than one virtual host so you can have something like:

	foobar.dev
	nyancat.dev
	blog.dev

Like when you're connecting to your database with sequelPro. You must treat your virtual machine like another computer. If you're using PHPupet it's quite easy. For this example my virtual machine has Ubuntu installed.

**Navigate to your project(s) folder**

mypath/puppet/hieradata

**Open common.yaml**

Under Vhosts you'll have something like this:

	vhosts:
        VO6aT11EHJmL:
            servername: localhost
            docroot: /var/www/public
            port: '80'
            setenv:
                - 'APP_ENV dev'
            override:
                - All
        4yNJr1LpLJYA:
            servername: blog.dev
            docroot: /var/www/vhosts/blog
            port: '80'
            setenv:
                - 'APP_ENV dev'
            override:
                - all

Each vhost is given a unique identification name and it can be anything. The options for servername, docroot seem simple, so we'll modify these.

Next for the virtual machine to recognize your updates make sure your vagrant is stopped while making these changes. After you're done restart vagrant. Once vagrant is up go into your directories where your sites-available directory is. In my case i'm using apache under ubuntu.

	/etc/apache2/sites-available

The files that you will see there, their name will match the unique names that you have in the common.yaml file except there are numbers in them for example:

	#-unique_name.conf

So in the common.yaml file if you created or modified settings under 4yNJr1LpLJYA you would need to look for #-4yNJr1LpLJYA.conf in this directory and match the settings as you have in your common.yaml file. Once you are done restart your server.

Also don't forget to add the virtual host into your local machines host file and match it with the same ip that puphet gave you (or that you configured).

Do this for each one that you want to add.

ps: if you know another way to manage vhosts quickly while using vagrant. Please, do comment and help a bother out.