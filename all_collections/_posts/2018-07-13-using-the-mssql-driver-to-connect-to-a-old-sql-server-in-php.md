---
layout: post
title: Using the MSSQL driver to connect to a old SQL server in PHP
date: 2018-07-13
tag: 2018,mssql,server,sysadmin,ubuntu
description: One of reasons we had to use PHP 5.6 in one of our recent projets was related to the fact that we needed to get info from the clients ERP,
author: Marco Monteiro
categories: [2018,mssql,server,sysadmin,ubuntu]
---

One of reasons we had to use PHP 5.6 in one of our recent projets was related to the fact that we needed to get info from the clients ERP, that one only allowed a connection via MSSQL. So after we got the [project running with PHP 5.6 instead of 7.2](https://blog.marcomonteiro.net/post/having-multiple-php-versions-on-your-dev-environment) we had to install the MSSQL drivers.

<!--more-->

Here's how.

This was done on Ubuntu 16.04 but I tested it on 18.04 too.

First, make sure you're up to date on all of your packages.

    $ sudo apt-get update
	$ sudo apt-get upgrade
	$ sudo apt-get dist-upgrade

Then we need to install all the FreeTDS & Dependencies.

	$ sudo apt-get install php5-sybase freetds-common libsybdb5
	$ sudo apache2ctl restart

Just restart apache and you should be good to go.

	$ sudo service apache2 restart

