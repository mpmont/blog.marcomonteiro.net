---
layout: post
title: A week on Manjaro Linux
date: 2020-11-07
tag: linux, distro, security, pacman, manjaro, arch
description: On the month of November I will be testing the Manjaro distribution
author: Marco Monteiro
categories: [ linux, distro, security, pacman, manjaro, arch ]
---

Last week I installed Manjaro Linux on my laptop and since then I've been using it as I would my work machine, even though I still use my desktop as my primary machine.

<!--more -->

I made my USB stick and went with the KDE version of Manjaro. The installation worked like a charm, even the live USB worked incredible.

Even thought I had my computer configured with my /home in another partition I decided to do a clean install and just format my home directory since if I end up installing it on my Desktop that's what I'll do.

After the install I updated the system, but a new version of Manjaro just came out, so I zero updates to do. I was not expeting that.

Then I started to tweak the KDE settings and most of all the "add/remove software" app, where you can configure how you wan your package manager to work.

I decided to enable pacman, AUR, flatpak and appImages.

Just a few momments later I started to install my software and adding my dotfiles from github.

First of all I was quite impressed with te amount of software available on pacman and AUR. I didn't have to add any sources like ppa on debian. Everything was avaiable and I could install it with one click or via terminal.

One basic example is docker and docker compose. Tools that I use everyday at work and at home. On debian based distros I had to read one or two pages of documentation to get them installed and working. On Manjaro?

    $ sudo pacman -S docker docker-compose

That's it!

So far first impressions are looking really good. I'm impressed with the package manager, the speed of everything, even the KDE theme is impressive.

Let's see how it goes next week.