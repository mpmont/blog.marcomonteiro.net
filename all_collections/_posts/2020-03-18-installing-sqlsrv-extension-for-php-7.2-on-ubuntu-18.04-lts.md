---
layout: post
title: Installing SQLsrv extension for PHP 7.2 on Ubuntu 18.04 LTS
date: 2020-03-18
tag: 2020,apache,linux,mssql,php,sqlsrv,ubuntu
description: One of our windows servers got updated to a more recent version of windows and SQLServer. Until then I was using the msSQL extension and was still on PHP 5.6
author: Marco Monteiro
categories: [2020,apache,linux,mssql,php,sqlsrv,ubuntu]
---

One of our windows servers got updated to a more recent version of windows and SQLServer. Until then I was using the msSQL extension and was still on PHP 5.6 on our intranet at work.

Since this update I decided to upgrade our servers too and move to PHP 7.2 and obviously to the SQLsrv extension.

<!--more-->

Let's assume that you already have PHP install and apache, so after that you should just do the following to get your microsoft packages.

On your server type the following commands:

    curl -s https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
	sudo bash -c "curl -s https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list"
	sudo apt-get update
	sudo ACCEPT_EULA=Y apt-get -y install msodbcsql17 mssql-tools
	sudo apt-get -y install unixodbc-dev

After this, you most likelly don't have the  the pecl7.X-sp command working. To solve this I did the following:

	sudo apt-get -y install gcc g++ make autoconf libc-dev pkg-config
	sudo apt-get install php-pear php-dev
	sudo pecl install sqlsrv
	sudo pecl install pdo_sqlsrv

After this all you need to do is create the necessary .ini file so that PHP can do its magic.

	sudo bash -c "echo extension=sqlsrv.so > /etc/php/7.2/mods-available/sqlsrv.ini"
	sudo ln -s /etc/php/7.2/mods-available/sqlsrv.ini /etc/php/7.2/apache2/conf.d/sqlsrv.ini
	sudo ln -s /etc/php/7.2/mods-available/sqlsrv.ini /etc/php/7.2/cli/conf.d/sqlsrv.ini
	sudo bash -c "echo extension=pdo_sqlsrv.so > /etc/php/7.2/mods-available/pdo_sqlsrv.ini"
	sudo ln -s /etc/php/7.2/mods-available/pdo_sqlsrv.ini /etc/php/7.2/apache2/conf.d/pdo_sqlsrv.ini
	sudo ln -s /etc/php/7.2/mods-available/pdo_sqlsrv.ini /etc/php/7.2/cli/conf.d/pdo_sqlsrv.ini

After this all you need to do is restart your apache:

	sudo service apache2 restart

That's it!

----

### Update for Ubuntu Server 20.04


Recently I needed to do this in a more recent version of Ubuntu Server, the lattest 20.04 LTS release. For this version there's only a few tweaks that you need to do. The first one is to change the packages list from Microsoft to the correct version. So instead of using this:

    sudo bash -c "curl -s https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list"

You should use:

    sudo bash -c "curl -s https://packages.microsoft.com/config/ubuntu/20.04/prod.list > /etc/apt/sources.list.d/mssql-release.list"

Then when installing the sqlsrv and pdo_sqlsrv now you need to specify a version, otherwise you'll get the following error:

    Notice: Trying to access array offset on value of type bool in PEAR/REST.php on line 187 PHP Notice: Trying to access array offset on value of type bool in /usr/share/php/PEAR/REST.php on line 187 No releases available for package "pecl.php.net/sqlsrv" install failed

To solve this head on to [this page](https://github.com/microsoft/msphpsql/releases) to check what is the more recent version. For me it was 5.9.0. So you need to install it like so:

    sudo pecl install sqlsrv-5.9.0
    sudo pecl install pdo_sqlsrv-5.9.0

To end this, the current version of PHP on Ubuntu Server 20.04 is 7.4, so all the symlinks should be created to the correct folder:

    sudo bash -c "echo extension=sqlsrv.so > /etc/php/7.4/mods-available/sqlsrv.ini"
    sudo ln -s /etc/php/7.4/mods-available/sqlsrv.ini /etc/php/7.4/apache2/conf.d/sqlsrv.ini
    sudo ln -s /etc/php/7.4/mods-available/sqlsrv.ini /etc/php/7.4/cli/conf.d/sqlsrv.ini
    sudo bash -c "echo extension=pdo_sqlsrv.so > /etc/php/7.4/mods-available/pdo_sqlsrv.ini"
    sudo ln -s /etc/php/7.4/mods-available/pdo_sqlsrv.ini /etc/php/7.4/apache2/conf.d/pdo_sqlsrv.ini
    sudo ln -s /etc/php/7.4/mods-available/pdo_sqlsrv.ini /etc/php/7.4/cli/conf.d/pdo_sqlsrv.ini

That's it, this is everything that changed for Ubuntu Server 20.04.