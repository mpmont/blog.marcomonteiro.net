---
layout: post
title: Need a legacy vagrant box?
date: 2016-08-06
tag: apache,box,mysql,phansible,php,vagrant
description: Last week I was contacted by some really old client. You know, the kind of client that you think that they don't even have the app you made for them
author: Marco Monteiro
categories: [apache,box,mysql,phansible,php,vagrant]
---

Last week I was contacted by some really old client. You know, the kind of client that you think that they don't even have the app you made for them online anymore.

Turns out, they do have such app online, and they wanted me to change some minor things in it. But obviously I couldn't do it directly in production. I needed to create a local environment that would mimic the one the client had.

<!--more-->

I havent developed anything in PHP 5.3 in a long time, and since I'm using vagrant mostly with [Phansible](http://phansible.com/) I couldnt create a machine with it. Because the oldest PHP version phansible supports is 5.4.

So I made a small box that supports what I needed and here's what you need to do:

### Download the box and init vagrant
	$ vagrant box add legacy-box https://www.dropbox.com/s/ch0rq7ajonkzimp/lucid64-lamp.box?dl=1
	$ vagrant init legacy-box

### Edit your vagrant file

	config.vm.network "private_network", ip: "192.168.33.10"
	config.vm.synced_folder "./", "/vagrant", type: "nfs"

### Boot up the machine

	$ vagrant up
	$ vagrant ssh

### You can add this to your provision id you want

	$ sudo apt-get install php5 // no futuro adicionar à provision
	$ sudo apt-get install php5-cli // no futuro adicionar à provision

### If you need mysql you might want yo edit your bindaddress so you can connect via ssh tunnel

	$ sudo nano /etc/mysql/my.cnf
	bindaddress passa de 127.0.0.1 a 0.0.0.0 // no futuro adicionar à provision

### With the lattest versions of vagrant using such a old version of ubuntu you might need to create this file with the following contents

	$ cat /etc/os-release
	NAME="Ubuntu"
	VERSION="12.04 LTS, Precise Pangolin"
	ID=ubuntu
	ID_LIKE=debian
	PRETTY_NAME="Ubuntu precise (12.04 LTS)"
	VERSION_ID="12.04"

### Exit and restart the machine

	$ exit
	$ vagrant reload

### Here's your default connection to mysql

	host: 127.0.0.1
	user: root
	password: password

	SSH host: 192.168.33.10
	SSH user: vagrant
	SSH pass: vagrant

Enjoy!