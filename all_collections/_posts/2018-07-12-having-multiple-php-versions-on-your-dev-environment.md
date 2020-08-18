---
layout: post
title: Having multiple PHP versions on your dev environment
date: 2018-07-12
tag: 2018,apache,lamp stack,php,sysadmin,ubuntu
description: There's one of our servers that we use to run small applications for a bunch of clients. At the time when we were configuring this server we ended up choosin
author: Marco Monteiro
categories: [2018,apache,lamp stack,php,sysadmin,ubuntu]
---

There's one of our servers that we use to run small applications for a bunch of clients. At the time when we were configuring this server we ended up choosin PHP 7.2.x as the version that would be used for these clients. However, once we started the development process we needed to connect to the clients ERP. Guess what? That connection needed php version 5.6.x max to work.

Here's the process to get everything up and running on Ubuntu 16.04, we also tested this on Ubuntu 18.04 and everything worked like a charm.

<!--more-->

Install apache:

    $ sudo apt update
    $ sudo apt install apache2 libapache2-mod-fastcgi

On some cases you'll get an error saying that you can't install libeapache2-mod-fastcgi.

    Package libapache2-mod-fastcgi is not available, but is referred to by another package.
    This may mean that the package is missing, has been obsoleted, or is only available from another source
     E: Package 'libapache2-mod-fastcgi' has no installation candidate

That can be resolved with the following:

    cd /tmp && wget http://mirrors.kernel.org/ubuntu/pool/multiverse/liba/libapache-mod-fastcgi/libapache2-mod-fastcgi_2.4.7~0910052141-1.2_amd64.deb
        sudo dpkg -i libapache2-mod-fastcgi_2.4.7~0910052141-1.2_amd64.deb; sudo apt install -f

The second step is to install PHP

For the installation of PHP versions, we use the PPA maintained here. Use the below couple of commands to add the PPA to your system.

    $ sudo apt install python-software-properties
	$ sudo add-apt-repository ppa:ondrej/php

We're almost there.

	$ apt update
	$ sudo apt install php5.6 php5.6-fpm
	$ sudo apt install php7.2 php7.2-fpm

Now we want to make sure everything is up and running:

	$ sudo systemctl status php5.6-fpm
	$ sudo systemctl status php7.2-fpm

Everything that is left to do is configure our Apache.

Enable few modules required for the configuration of multiple PHP versions with Apache. These modules are necessary to integrate PHP FPM and FastCGI with Apache server.

        $ sudo a2enmod actions fastcgi alias proxy_fcgi

In our www folder we create two projects. Lets say for the sake of this example its something like this:

	$ sudo mkdir /var/www/php5
	$ sudo mkdir /var/www/php7

Now, create and index.php containing the phpinfo() function on each one.

Let’s start the creation of VirtualHost. Apache keeps all the VirtualHost configuration files under /etc/apache2/sites-available with the extension .conf. Create a file for the first virtual host and edit in your favorite text editor.

	$ sudo vim /etc/apache2/sites-available/php5.local.conf

Add the following content. Make sure to use correct ServerName and directory path according to your setup. This website is configured to work with PHP 5.6.

      <VirtualHost *:80>
	  ServerName php5.local
	  DocumentRoot /var/www/php5
	  <Directory /var/www/php5>
		  Options -Indexes +FollowSymLinks +MultiViews
		  AllowOverride All
		  Require all granted
	  </Directory>
	  <FilesMatch \.php$>
		  # Apache 2.4.10+ can proxy to unix socket
		  SetHandler "proxy:unix:/var/run/php/php5.6-fpm.sock|fcgi://localhost/"
	  </FilesMatch>
  </VirtualHost>

  Same thing for the other one with a different path and different PHP version.

 	$ sudo vim /etc/apache2/sites-available/php7.local.conf


    <VirtualHost *:80>
    ServerName php7.local
    DocumentRoot /var/www/php7
    <Directory /var/www/php7>
        Options -Indexes +FollowSymLinks +MultiViews
        AllowOverride All
        Require all granted
    </Directory>
    <FilesMatch \.php$>
        SetHandler "proxy:unix:/var/run/php/php7.2-fpm.sock|fcgi://localhost/"
    </FilesMatch>
</VirtualHost>


Restart apache to get everything up and running.

        $ sudo service apache2 restart

Job done. Now you have two applications running different PHP versions on the same machine.

