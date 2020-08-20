---
layout: post
title: Using PuPHPet and then connecting to your mysql via SSH tunnel
date: 2016-02-21
tag: mysql,php,puphpet,vagrant
description: I just did a fresh install of vagrant and built it using the online tool from PuPHPet
author: Marco Monteiro
categories: [mysql,php,puphpet,vagrant]
---

I just did a fresh install of vagrant and built it using the online tool from PuPHPet. Had everything ready but I wasn't able to connect to my mysql server.

<!--more-->

The problem was in my SSH password. I thought it was this one:

    u. vagrant
	p. vagrant

But for some reason it wasn't (yes it was left it as the default one from PuPHPet). So for consistency now everytime I do a fresh install I  always do a few things; Access my machine via SSH.

        $ vagrant ssh

Changing the way your server deals with mysql connections.

        $ sudo nano /etc/mysql/my.cnf

Here you want to find the bindaddress setting which will be set to 127.0.0.0 and change it to 0.0.0.0. Don't forget to restart the mysql server after this.

        $ sudo service mysql restart


Anythins left to do is change your password to "vagrant" for consistency.

        $ passwd

That's it, now you can connect without any problems via SSH tunnel to your mysql.