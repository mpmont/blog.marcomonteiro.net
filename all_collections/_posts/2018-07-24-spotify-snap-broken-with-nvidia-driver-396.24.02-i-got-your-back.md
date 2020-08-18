---
layout: post
title: Spotify snap broken with Nvidia driver 396.24.02? I got your back.
date: 2018-07-24
tag: 2018,nvidea,spotify,ubuntu
description: Upgraded my Nvidia driver just now from 396.24.0 to 396.24.02, rebooted, and Spotify no longer works. It opens a window but never draws anything but a black screen.
author: Marco Monteiro
categories: [2018,nvidea,spotify,ubuntu]
---

Upgraded my Nvidia driver just now from 396.24.0 to 396.24.02, rebooted, and Spotify no longer works. It opens a window but never draws anything but a black screen.

<!--more-->

    $ snap run spotify
	Gtk-Message: Failed to load module "gail"
	Gtk-Message: Failed to load module "atk-bridge"
	Gtk-Message: Failed to load module "canberra-gtk-module"
	ATTENTION: default value of option force_s3tc_enable overridden by environment.
	libGL error: No matching fbConfigs or visuals found
	libGL error: failed to load driver: swrast
	[0604/185738.869585:ERROR:gl_context_glx.cc(227)] Couldn't make context current with X drawable.
	[0604/185738.869619:ERROR:gpu_info_collector.cc(62)] gl::GLContext::MakeCurrent() failed
	[0604/185746.603499:ERROR:browser_gpu_channel_host_factory.cc(120)] Failed to launch GPU process.

![screenshot](https://i.imgur.com/p0yeYFe.png)

The solution is quite simple. Until fixed snaps are available, you can start spotify without GPU accelerated graphics.

	$ snap run spotify --disable-gpu

<small><strong>Update:</strong> Since 06/08/2018 spotify is working fine with the new drivers!</small>

