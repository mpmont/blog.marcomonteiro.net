---
layout: post
title: Using the Codeigniter 4 standard on your projects with Sublime Text
date: 2020-09-01
tag: blog,codeigniter 4, standard
description: Ive been using phpfmt for a while, however we now moved to codeigniter 4 that provides actual standards that can be used with sublike
author: Marco Monteiro
categories: [ blog,codeigniter 4, standard ]
---

We moved to Codeigniter 4 for our new projects. Until now, we've using phpfmt so everyone in the team can use the same standard while coding.

However Codeigniter 4 has it's own standard and it just makes sense for us to move to that new standard.

For this we need:

1. [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer/)
1. [Codeigniter4-Standard](https://github.com/codeigniter4/coding-standard)
1. [PHP-CS-Fixer](https://github.com/FriendsOfPhp/PHP-CS-Fixer)
1. [Sublime-phpcs](https://packagecontrol.io/packages/Phpcs)

There's a few ways we can go about this, but since this was something that we actually need to use on a bunch of projects I going with installing all this globally.

### **1. PHP Code Sniffer**

PHP_CodeSniffer requires PHP version 5.4.0 or greater, although individual sniffs may have additional requirements such as external applications and scripts. See the Configuration Options manual page for a list of these requirements.

If you're using PHP_CodeSniffer as part of a team, or you're running it on a CI server, you may want to configure your project's settings using a configuration file.

    $ composer global require "squizlabs/php_codesniffer=*"

### **2. Codeigniter 4 - Coding Standard**

Using composer this can also be installed globally.

    $ composer global require codeigniter4/codeigniter4-standard

### **3. PHP CS Fixer**

To install PHP CS Fixer, install Composer and issue the following command:

    $ composer global require friendsofphp/php-cs-fixer

Then make sure you have the global Composer binaries directory in your PATH. This directory is platform-dependent, see Composer documentation for details. Example for some Unix systems:

    $ export PATH="$PATH:$HOME/.composer/vendor/bin"

### **4. Sublime-phpcs package**

Open your sublime text and install this package. After that you want to to open the user setting and change the following:


You should pay special attention to the following setting:

    "phpcs_executable_path": "/home/marco/.config/composer/vendor/squizlabs/php_codesniffer/bin/phpcs",
    "phpcs_additional_args": {
        "--standard": "/home/marco/.config/composer/vendor/codeigniter4/codeigniter4-standard/CodeIgniter4",
        "-n": ""
    },
    "php_cs_fixer_executable_path": "/home/marco/.config/composer/vendor/friendsofphp/php-cs-fixer/php-cs-fixer",
    "phpcbf_executable_path": "/home/marco/.config/composer/vendor/squizlabs/php_codesniffer/bin/phpcbf",
    "phpcbf_additional_args": {
        "--standard": "/home/marco/.config/composer/vendor/codeigniter4/codeigniter4-standard/CodeIgniter4",
        "-n": ""
    },

The paths should be the ones you have on your system. I'm on linux, so the composer installed globally are in my .config. If you're on windows or mac your paths might differ.
