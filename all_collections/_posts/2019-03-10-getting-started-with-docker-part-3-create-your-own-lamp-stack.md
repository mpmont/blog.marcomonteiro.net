---
layout: post
title: Getting started with Docker part 3 - Create your own lamp stack
date: 2019-03-10
tag: docker
description: Let's work on the following scenario. You are a PHP developer and need a Lamp stack environment to work with. That means you need Linux, Apache, MariaDB or Mysql and
author: Marco Monteiro
categories: [docker]
---

Let's work on the following scenario. You are a PHP developer and need a Lamp stack environment to work with.

That means you need Linux, Apache, MariaDB or Mysql and PHP.

So let's get this show on the road and create our own lamp stack.

<!--more-->

First lets create a project forlder, this can be in any place you want.

    $ mkdir -p lamp-stack/DocumentRoot
	$ echo "<?php phpinfo(); ?>" > lamp-stack/DocumentRoot/index.php

Basically your DocumentRoot will be your working environment. Now we must create two files, those will be placed on your root project folder.

- docker-compose.yml
- ./php-apache/Dockerfile

Let's start with the docker-compose.yml file.

	version: '3'
	services:
		php-apache:
			build:
				context: ./php-apache
			ports:
				- 80:80
			volumes:
				- ./DocumentRoot:/var/www/html
			links:
				- 'mysql'

		mysql:
			image: mysql
			volumes:
				- ./db:/var/lib/mysql
			command: --default-authentication-plugin=mysql_native_password
			restart: always
			ports:
				- 3306:3306
			environment:
				MYSQL_ROOT_PASSWORD: root

1st line we need to define the sintax version we're working with.
2nd We have the list of our services. These are php-apache and mysql (you can name these however you want).

For the "php-apache" we have 3 items, **build** (where we reference the folder php-apache where the dockerfile is);

**Ports** basically telling it to map your port 80 to the exact same port inside the docker container.

**Volumes**, this is where we map our own projecto folder to the docker container one.

**Links**, this basically tells it to run the second service as a dependent one from the php-apache.

The mysql is basically a direct copy from the [https://hub.docker.com](https://hub.docker.com/_/mysql) you should really get familiar with this service.

Finally our dockerfile. This has all the comands you want to run for your php environment.

    FROM php:7.2.1-apache
	MAINTAINER egidio docile
	RUN docker-php-ext-install pdo pdo_mysql mysqli
	RUN a2enmod rewrite

Firs we define our php version (this can be whatever you want to work with). The maintainer of it and then the list of php extensions we need. You can add as many as you like.

Here's your final folder structure:

![Folder structure](https://i.imgur.com/4MxbwGV.png)

All you need to do now is start your docker container. You do this by going inside your project folder and running the following command.

	$ sudo docker-compose up

The first time you do it, this may take a while.

Now to access your project just go to http://localhost. And to access your mysql server just connect as usual using your application of choice.