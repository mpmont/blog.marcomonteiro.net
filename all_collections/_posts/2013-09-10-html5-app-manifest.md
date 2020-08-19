---
layout: post
title: HTML5 App Manifest
date: 2013-09-10
tag: firefox OS,html5,mobile,tips
description: We all have our applications and we all want then to be always using the best tools, but most of all, we all want our content to get to everyone.
author: Marco Monteiro
categories: [firefox OS,html5,mobile,tips]
---

We all have our applications and we all want then to be always using the best tools, but most of all, we all want our content to get to everyone.

That's why we add social sharing functionality, or iox capability so our application can turn into a web app in our phone. However, there are now more and more platforms to deal with, and many more to come. So today I'm going to give you a little snippet so you can turn your website into a HTML5 app. This way your website will run as a "native app" on the new Firefox OS.

<!--more-->

Mozilla's awesome new HTML5-based mobile operating system, Firefox OS, is going to be a game-changer in the mobile app space. No more needing to write "native" code for each device, no more reliance on PhoneGap to be a first-class device language. Better yet, essentially all you need to do to make your existing website or web app a Firefox OS app is add a manifest.webapp file to your domain which looks similar to this:

 	 {
		"version": "1.0",
		"name": "Your App Name",
		"description": "Your new awesome HTML5-based mobile web app!",
		"launch_path": "/index.html",
		"icons": {
			"16": "/img/mylogo-16.png",
			"48": "/img/mylogo-48.png",
			"128": "/img/mylogo-128.png"
		},
		"developer": {
			"name": "Developer Name",
			"url": "http://yourawesomeapp.com"
		},
		"installs_allowed_from": ["*"],
		"locales": {
			"pt": {
				"description": "A minha nova app",
				"developer": {
					"url": "http://yourawesomeapp.com"
				}
			},
			"en": {
				"description": "My new web app",
				"developer": {
					"url": "http://yourawesomeapp.com"
				}
			}
		},
		"default_locale": "en"
  	}

It really can't get any easier! To guard yourself against problem when your app is used offline, be sure to include the [HTML standard appcache](https://developer.mozilla.org/en-US/docs/HTML/Using_the_application_cache) too!

This article it's a part of a series of small articles showing how to make your website more mobile compatible.