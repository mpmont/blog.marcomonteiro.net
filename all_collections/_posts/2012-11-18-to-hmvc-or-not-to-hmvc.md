---
layout: post
title: To HMVC or not to HMVC?
date: 2012-11-18
tag: codeigniter,frameworks,hmvc,laravel,mvc
description: I’ve been trying some stuff out on Laravel 3 and also Laravel 4. One thing that I like about laravel 3 is the use of bundles. Making it easy to
author: Marco Monteiro
categories: [codeigniter,frameworks,hmvc,laravel,mvc]
---

I’ve been trying some stuff out on Laravel 3 and also Laravel 4. One thing that I like about laravel 3 is the use of bundles. Making it easy to re-use your code, which makes the application modular and so forth.
While in Codeigniter I never missed this feature, well at least not until I had a taste of what it really was using other frameworks. Now I think I’m going to try and use the HMVC pattern with Codeigniter.

When I first made my research I ended up here: codeigniter modular extensions hmvc after reading the wiki and talking about it with the folks at #codeigniter (Freenode) I think this is the way to go.
<!--more-->
**So what is this HMVC thing?**

Modular HMVC means modular MVC triads. Modular Separation and Modular Extensions allows related controllers, models, libraries, views, etc. to be grouped together in module directories and used like a mini application. But, Modular Extensions goes one step further and allows those modules to ...talk“ to each other. You can get controller output without having to go out through the http interface again.
I think on my next project I’m going to stop using sparks and MVC. I shall embrace composer and HMVC. Until now I’ve been using composer and sparks at the same time but that’s gotta stop.