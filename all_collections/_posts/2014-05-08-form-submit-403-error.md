---
layout: post
title: Form Submit == 403 Error?
date: 2014-05-08
tag: apache,mod_security,server,web,Webdev
description: From time to time, I have to work on a really crappy server. They have the weirdest rules of all, they're obssed with security. I don't have a right to
author: Marco Monteiro
categories: [apache,mod_security,server,web,Webdev]
---

From time to time, I have to work on a really crappy server. They have the weirdest rules of all, they're obssed with security. I don't have a right to see logs, they randomly block my IP from time to time. I can't even call [phpinfo()](http://pt1.php.net/phpinfo). Yeah, that bad!

Today I ran into a problem that made me go mad. I had a simple form with just a few fields. Locally the form was submiting via *[$_POST](http://www.php.net/manual/en/reserved.variables.post.php)* and everything was great.

<!--more-->

But when I pushed my code to that server I couldn't submit anything. The server was not getting the *[$_POST](http://www.php.net/manual/en/reserved.variables.post.php)* and it was interpreting everything as *[$_GET](http://www.php.net/manual/en/reserved.variables.get.php)*.

Turns out they turned on [mod_security](http://en.wikipedia.org/wiki/ModSecurity) and one of my fields was supposed to be a url. But for some scurity reason if one of my input fields had *http://* in it, they blocked the request.

First thing that came to mind: remove the *http://* with javascript before submit and then add it back when I need it.

But that's just nonsense!

Turns out if I have my input field called *something_url* the [mod_security](http://en.wikipedia.org/wiki/ModSecurity) will be expecting the value to be one url and it will not block my request.

So here's my tip, if you have a project that you're deploying to a server that you have no control of, everytime you have a input that will be used to insert a url, you should "always" shove the sufix _url.
