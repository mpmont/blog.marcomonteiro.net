---
layout: post
title: Animations using CSS3
date: 2013-10-02
tag: animations,css,css3,libraries,tips
description: Im not a big fan of big animations on websites. I like to get in, get the thing I was looking for and get out. I hate it if I
author: Marco Monteiro
categories: [animations,css,css3,libraries,tips]
---

I'm not a big fan of big animations on websites. I like to get in, get the thing I was looking for and get out. I hate it if I have to look at your awesome loading animation if the thing I just want is to look at your contacts page.

However, from time to time, we need to animate some small elements. These days you can do most of it with just CSS3. People are using less and less javascript for this.

<!--more-->

But, once again, we're (lazy) developers, so we don't want to make our animations from scratch.

Well Justin Aguilar got you covered, he compiled CSS3 Animation Cheat Sheet that is a set of preset, plug-and-play animations for your web projects. All you need to do is add the stylesheet to your website and apply the pre-made CSS classes to the elements you want animated.

The CSS3 Animation Cheat Sheet uses CSS3 @keyframes and works on all the latest browsers (that's IE 10). Using CSS3 @keyframes, you don't have to worry about positioning the element to accommodate the animations - it will animate into place. Also for users with older browsers, the animated element will be visible and in place, even if the animation doesn't trigger. Below are instructions on how to get started.

[<i class="icon-external-link"></i> The project](http://www.justinaguilar.com/animations/index.html)

[<i class="icon-css3"></i> The css file](http://www.justinaguilar.com/animations/index.html#download)

However, there's another project that you might want to take a look when it comes to animations done with CSS3.

**It's called animo.js**

This one is a small javascript library that is used to trigger CSS3 animations. The documentation is near perfect but this one I haven't tested it yet.

This library solves the main problem with CSS3 animations. The problem with CSS alone is that they're usually fired on page load or a hover event, and you can't stack animations or trigger another when one has completed. That's where JavaScript and animo come in. You can easily stack animations to fire one after another, specify callbacks for the completion of an animation, or simply fire animations on any event or at any moment you please.

[<i class="icon-external-link"></i> Animo.js website](http://labs.bigroomstudios.com/libraries/animo-js)

[<i class="icon-github"></i> Animo.js repository](https://github.com/ThrivingKings/animo.js)