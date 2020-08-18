---
layout: post
title: $ exa A modern replacement for ls
date: 2020-04-17
tag: 2020,linux,terminal,ubuntu
description: You list files hundreds of times a day. Why spend your time squinting at black and white text? exa is an improved file lister with more features and better defaults.
author: Marco Monteiro
categories: [2020,linux,terminal,ubuntu]
---

You list files hundreds of times a day. Why spend your time squinting at black and white text?

exa is an improved file lister with more features and better defaults. It uses colours to distinguish file types and metadata. It knows about symlinks, extended attributes, and Git. And it’s small, fast, and just one single binary.

<!--more-->

exa is written in Rust. So you'll need that first in case you don't already have it.

Run the following command (assuming you have curl installedo on your system) to get started with the installation of Rust in your ubuntu based server/pc:

	$ curl https://sh.rustup.rs -sSf | sh

Now you need to download the lattest version of exa. Head on to [their github page](https://github.com/ogham/exa/releases) and download the lattest version.

Just copy the download link and download the zip using wget, for example with the v0.9.0 you can download the binary with the following command (you can switch to a temporary directory and download the zip in there):

	# You should check your own version of this.
	$ wget -c https://github.com/ogham/exa/releases/download/v0.9.0/exa-linux-x86_64-0.8.0.zip

Then, unzip the binary:

	$ unzip exa-linux-x86_64-0.8.0.zip

The zip contains a single file, namely the binary exa-linux-x86_64. So the last step is to move it to the bin directory of the local user so it will be accesible later in the cli as exa with the following instruction:

	$ sudo mv exa-linux-x86_64 /usr/local/bin/exa

To use this all you need is to type exa on your terminal. However what you can do to make the change even more perminante is to alias ls to axa.

To do that I went to my .zshrc file and added the following:

	alias ls='exa --long --header --git'

This way you can use your ls command like you always did and it will be translated into exa.

![exa](https://i.imgur.com/VXTYKQl.png)

Exa supports the following main features:

**Colours**

Different types of file and data will be coloured differently, and the user and group columns will be highlighted for the current user.

**All the information**

exa can display a file’s extended attributes, as well as standard filesystem information such as the inode, the number of blocks, and a file’s various dates and times.

**It's fast**

exa queries files in parallel, giving you performance on par with ls.

**Tree view**

Not only is the standard tree tool built-in, but it’ll show you your files’ information alongside the hierarchy.

**Git support**

View the staged and unstaged status of every file, right there in the standard view. Also works in tree view for a high-level overview of your repository.

**Wide view**

How many columns can you display in your terminal at once? How many do you need?