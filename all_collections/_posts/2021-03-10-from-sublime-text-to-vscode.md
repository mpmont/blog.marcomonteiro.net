---
layout: post
title: From Sublime Text 3 to Visual Studio Code
date: 2021-03-10
tag: linux, webdev, php, editor, sublime, vscode
description: Recently I've been learning a bit of Angular, and with I tried vscode due to its intelisense properties.
author: Marco Monteiro
categories: [ linux, webdev, php, editor, sublime, vscode ]
---
I've been a Sublime Text user since version 2. I was a early adopter of that version and used it for at least 9 years now. This month I decided to try something new and opt-in for visual studio code.

<!--more-->

For the last month or so I've been learning a bit of Angular along my team. With it we decided to try vscode mostly for its intelisense features when working with JavaScript.

At first I didn't like it that much, but then I started to fidle with it and it grew on me. Then if I was to move to it full time I had to make it behave well with our team standards, regarding code standards and stuff like that. **Here's what I did.**

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Look and Feel</u></strong></h3>

I used the same exact theme on sublime and font for a few years. It takes quite a while for me to change that. 

The theme I use is called **Material Theme**. You can find the link [here](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme). You can install that with just one line.

Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

    ext install Equinusocio.vsc-material-theme

With it I also installed the propper icons for the material theme, [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme).

Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

    ext install PKief.material-icon-theme

Then I had to fix the problem with the wasted space on the sidebar. Vscode by default has this bar called activity bar, where you can go from file manager, to version control and your settings. I could just hide it but I didn't want to have to use my mouse to hide and show that bar. Then I found and extension called [Costumize UI](https://marketplace.visualstudio.com/items?itemName=iocave.customize-ui). With it you can move that bar to the bottom part of your sidebar. 

![Costumize UI](https://raw.githubusercontent.com/iocave/customize-ui/master/screenshot.png)

This was gold, because now I can just toggle the sidebar with ctrl+b and this bar goes along with it.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>PHP Development</u></strong></h3>

After this step my install of vscode looks exactly like sublime text 3 and the transition was going good.

Then I needed to install some extensions more towards the PHP development than.

First installed the PHPDoc Comment this helps with writing documentation for your code. 

Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

    ext install rexshi.phpdoc-comment-vscode-plugin

![Dockblocker](https://raw.githubusercontent.com/shishirui/phpdoc-comment-vscode-plugin/master/images/preview.gif)

Then the main reason we moved to vscode. It's called [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client). This is PHP code intelligence for Visual Studio Code. Intelephense is a high performance PHP language server packed full of essential features for productive PHP development.

Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

    ext install bmewburn.vscode-intelephense-client

In our team are using PHPfmt for our PHP projects and this is something that we absolutely needed to continue using with the same settings. This is very important so can maintain the same file formats on any project we open and use.

After this I changed a bunch of settings in the editor to suit my needs. Here's my complete settings.json file. 


<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Complete settings</u></strong></h3>

    {
        "editor.fontFamily": "'M+ 1mn light', 'Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback'",
        "editor.minimap.enabled": false,
        "php.executablePath": "/usr/bin/php7",
        "workbench.colorTheme": "Material Theme",
        "workbench.iconTheme": "material-icon-theme",
        "editor.cursorBlinking": "smooth",
        "files.exclude": {
            "*.exe": true,
            "*.pyo": true,
            "**/.pyc": true
        },
        "editor.rulers": [
            80,
            120
        ],
        "diffEditor.wordWrap": "on",
        "phpfmt.php_bin": "/usr/bin/php7",
        "phpfmt.passes": [
            "ConvertOpenTagWithEcho",
            "PrettyPrintDocBlocks",
            "ReturnNull",
            "OnlyOrderUseClauses"
        ],
        "editor.formatOnSave": true,
        "[php]": {
            "editor.defaultFormatter": "kokororin.vscode-phpfmt"
        },
        "editor.lineHeight": 24,
        "composer.executablePath": "/usr/local/bin/composer",
        "gitlens.hovers.currentLine.over": "line",
        "gitlens.currentLine.enabled": false,
        "gitlens.codeLens.enabled": false,
        "gitlens.statusBar.enabled": false,
        "gitlens.hovers.enabled": false,
        "gitlens.blame.toggleMode": "window",
        "gitlens.changes.toggleMode": "window",
        "grunt.autoDetect": "off",
        "editor.wordWrap": "on",
        "customizeUI.stylesheet": {
            "workbench.useExperimentalGridLayout": true
        },
        "editor.multiCursorModifier": "ctrlCmd",
        "customizeUI.activityBar": "bottom",
        "window.zoomLevel": 2,
        "editor.fontSize": 15,
        "editor.folding": false,
        "editor.glyphMargin": false,
    }
