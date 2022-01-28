---
layout: post
title: How to use LSP-intelephense in Sublime Text 4
date: 2022-01-28
tag: linux, webdev, php, sublime, LSP-intelephense
description: PHP support for Sublime's LSP plugin provided through intelephense.
author: Marco Monteiro
categories: [ linux, webdev, php, sublime, LSP-intelephense ]
---
Always wandered how to setup LSP-Intelephense in Sublime Text 4 so you can have propper validation and code completion? I got you covered.

<!--more-->

There's a few requirements to do this. First you need to install LSP globally in your machine. To do this you need to do the following:

    $ cd ~/
    $ mkdir .phpactor
    $ cd .phpactor
    $ git clone git@github.com:phpactor/phpactor
    $ cd phpactor
    $ composer install
    $ cd /usr/local/bin
    $ sudo ln -s ~/.phpactor/phpactor/bin/phpactor phpactor

This will make phpactor avaiable globally. To do a small health check on the binary that you just installed go into a project you're using. Phpactor works best when used with Composer, and is slightly better when used with Git.

Check support using the status command:

    $ phpactor status
    ✔ Composer detected - faster class location and more features!
    ✔ Git detected - enables faster refactorings in your repository scope!

You might get a different output saying tha there's some config files missing, but that's not a problem.

After this you need to install 3 sublime packages.

* [LSP](https://packagecontrol.io/packages/LSP)
* [LSP-intelephense](https://packagecontrol.io/packages/LSP-intelephense)

After that you need to restart sublime text.

Configuration

Configure the intelephense language server by accessing Preferences > Package Settings > LSP > Servers > LSP-intelephense.

Also in your Preferences > Package Settings > LSP

    // Settings in here override those in "LSP/LSP.sublime-settings"
    {
        "clients": {
            "phpactor": {
                "enabled": true,
                "command": ["/usr/local/bin/phpactor", "language-server"],
                "selector": "source.php"
            }
        }
    }

Now play with the settings to your needs.