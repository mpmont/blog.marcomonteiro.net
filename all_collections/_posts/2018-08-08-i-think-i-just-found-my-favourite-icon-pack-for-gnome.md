---
layout: post
title: I think I just found my favorite icon pack for gnome
date: 2018-08-08
tag: 2018,gnome,iconpack,linux,ubuntu
description: Presenting Flat Remix. Flat remix is a pretty simple icon theme inspired on material design. It is mostly flat with some shadows, highlights and gradients for some depth and uses
author: Marco Monteiro
categories: [2018,gnome,iconpack,linux,ubuntu]
---

Presenting [Flat Remix](https://github.com/daniruiz/flat-remix). Flat remix is a pretty simple icon theme inspired on material design. It is mostly flat with some shadows, highlights and gradients for some depth and uses a colorful palette with nice contrasts.

<!--more-->

![Flat remix](https://raw.githubusercontent.com/daniruiz/Flat-Remix/master/preview.png)

Flat Remix icon theme is available in three variants:

1. Flat Remix - main icon theme
1. Flat Remix Dark - for dark interfaces
1. Flat Remix Light - for light interfaces

**Terminal installation**

	$ cd /tmp && rm -rf flat-remix &&
	git clone https://github.com/daniruiz/flat-remix &&
	mkdir -p ~/.icons && cp -r flat-remix/Flat-Remix* ~/.icons/ &&
	gsettings set org.gnome.desktop.interface icon-theme "Flat-Remix"

**Ubuntu based distributions**

	$ sudo add-apt-repository ppa:daniruiz/flat-remix
	$ sudo apt-get update
	$ sudo apt-get install flat-remix