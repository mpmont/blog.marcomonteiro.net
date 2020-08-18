---
layout: post
title: Javascript is basically cancer!
date: 2018-09-11
tag: 2018,cancer,chrome,internet,javascript
description: Most of us these days have loads of RAM to spare on our laptops and desktops. But do you remember a time when you had a computer just to do
author: Marco Monteiro
categories: [2018,cancer,chrome,internet,javascript]
---

Most of us these days have loads of RAM to spare on our laptops and desktops. But do you remember a time when you had a computer just to do some web browsing and just 2GB of ram was what you needed?

These days you have just a few tabs open on your browser and you can see the ram just going up and up.

<!--more-->

A good example on this is reddit. Reddit was a lightweight website (client side) but these days if you have a thread open and looking at the contents of your RAM you can see that the page alone claims around 236MB of data. The majority of it is objects that the various JS scripts on the webpage created long after the page was actually downloaded.

I normally never have more than 15 chrome tabs open and this is what that looks.

![htop](https://i.imgur.com/M8mG9BN.png)

Websites are getting heavy and JS frameworks are a core problem of it. Turn off JavaScript in your browser and watch how quickly the RAM usage drops to near nothing, and that's the core issue here. JavaScript has become this massive beast that just gets worse each year that goes by as devs pile more and more "features". Just as a test I turned JavaScript off, opened 38 tabs (different news sites, tech companies like Apple/Microsoft/Dell... and a few programming sites python, w3, etc...) Total weight of Chome in RAM, ~650MB.

To say JavaScript is getting out of hand really undersales the issue. JavaScript has reached nightmarishly abusive levels. Heck a lot of sites (imgur) won't even do anything unless you turn on JavaScript and then when you do, the site by itself wrecks havoc with your RAM. To compound issues, some sites will load into memory eight different fuzzy fonts that's specific to just that site that you are on, and the worst are when that font is used for at most 400 bytes worth of text. You are left saying to yourself, "Seriously website? You downloaded a 3.8MB font file and loaded into memory just so you could render 400 bytes in foo-foo font? You could have just made a 1.8KB jpeg for 100 different languages and loaded the one image or FFS all 100 images, and it would still be more lightweight than 3.8MB of font that I'll more than likely never notice!"

I'm not trying to make excuses for browsers, they ought to release resources a bit quicker or at least provide a slider that allows the user to make that call (because web browsers aren't exactly sure if you'll hit the back button or not, so it holds on to those resources for a good deal of time because reloading those resources could be a significant performance hit) and then sometimes folks get into the apologist stance and say, "well unused RAM is bad RAM." But the bigger point folks should focus on is how absolutely insanely ginormous webpages have become, and the abusive JS frameworks that are massive and create 1000s of objects just to do a simple task is single handedly the biggest reason your web browser is eating RAM faster than Charlie Sheen can snort cocaine.

Now I'm not saying that we should stick to website that are just plain text to cut on some ram. There's use cases where that heavy usage of javascript is just amazing. Take a look at websites like Twitch, Netflix or even something like Google Drive.

Do me a big favor, next time you just npm install the latest framework and all associated dependencies if you don't understand the overhead and runtime consequences of implementing that code in an objectively shitty language you are basically ruining the web. It needs to be stripped back again. When your bundle.js ginormous you need to rethink your strategy.
