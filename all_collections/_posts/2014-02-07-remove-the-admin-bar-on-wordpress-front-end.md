---
layout: post
title: Remove the admin bar on wordpress
date: 2014-02-07
tag: blog,tips,wordpress
description: Yes, lately I've been doing some Wordpress stuff. Before you start throwing stones, I'm not doing the kind of stuff to be ashamed about. I'm actually building some blogs.
author: Marco Monteiro
categories: [blog,tips,wordpress]
---

Yes, lately I've been doing some Wordpress stuff. Before you start throwing stones, I'm not doing the kind of stuff to be ashamed about. I'm actually building some blogs.

One thing that bothers me a lot is the admin bar on the front-end, always there, always present. Fucking up my css.

<!--more-->

I looked around a little bit and I found this:

		add_filter('show_admin_bar', '__return_false');

Just shove that in your wp-config.php file and you'll be good to go.

< sarcasm >How awesome is wordpress right?</ sarcasm >