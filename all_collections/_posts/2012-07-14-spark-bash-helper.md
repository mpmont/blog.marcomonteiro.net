---
layout: post
title: Spark bash helper
date: 2012-07-14
tag: ci,code,codeigniter,screencasts
description: While chilling around in #codeigniter on freenode, I was talking with Josh Manders aka killswitch about Sparks and he noticed how cumbersome
author: Marco Monteiro
categories: [ci,code,codeigniter,screencasts]
---

<iframe src="https://player.vimeo.com/video/45780191?color=ffffff" width="100%" height="375" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>

While chilling around in #codeigniter on freenode, I was talking with Josh Manders aka killswitch about Sparks and he noticed how cumbersome it is, so he set out to learn Bash and started creating this script to make it easier to use Spark.

<!--more-->

Right now it allows you to install Spark into your CodeIgniter directory, and then use the Spark commands right in the script. Couple of them have been redone, like the install/remove/version commands.

**There's a lot of stuff that Josh want's to add to the project like:**

* Add a way to find the latest spark version and use that when doing “spark install example-spark” that way you do not need to specify the version. (Why this doesn’t already exist with spark is beyond me.)
* Check for dependancies of OS installed, such as wget, php, etc.
* Check to see if you’re in a proper CodeIgniter project folder.

[Fork the project](https://github.com/killswitch/spark) and add awesomeness to it.
Follow [Josh on Github](https://github.com/killswitch).