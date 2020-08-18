---
layout: post
title: Sublime pro tip CTags
date: 2013-06-06
tag: osx,package,Sublime Text,text-editor
description: One of the best features about the new version of Sublime that is now in beta is probably the goto definition. That was actually the main feature that was making
author: Marco Monteiro
categories: [osx,package,Sublime Text,text-editor]
---

One of the best features about the new version of Sublime that is now in beta is probably the goto definition. That was actually the main feature that was making me consider the update.
However, now you can have that feature in your sublime text 2 powered by CTags.

The ctags command is searched for on the system PATH. It works by doing a binary search of a memory-mapped tags file, so it will work efficiently with very large (50MB+) tags files if needed.
<!--more-->

To install the package you can do it in two ways. Either use the package manager or just clone the repository into your Packages directory.

If like me anyone is having trouble getting the CTags -R flag to work on OSX, you are probably using the stock CTags installation.

To get a proper copy of ctags, use one of the following options:

**Using Homebrew:**

		brew install ctags

**Using MacPorts:**

		port install ctags

Make sure that Sublime Text is using the right version of CTags:

If ‘which ctags’ doesn’t point at ctags in ‘/usr/local/bin’, make sure you add ‘/usr/local/bin’ to your PATH ahead of the folder ‘which ctags’ reported.

Add or modify the ‘export PATH=…’ (e.g. in /.profile) to make the change permanent

Also if you installed it via brew you may want to add this to your alias list:

		$ alias ctags="`brew --prefix`/bin/ctags"

**Usage**

This uses .tags files created in ctags -R -f .tags recursive mode (by default).

The plugin will try to find a .tags file in the same directory as the current view, walking up directories until it finds one. If it can’t find one it will offer to build one ( in the directory of the current view ).

[<i class="icon-link"></i> CTags ](https://github.com/SublimeText/CTags)