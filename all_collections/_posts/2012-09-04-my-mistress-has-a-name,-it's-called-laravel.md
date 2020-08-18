---
layout: post
title: My mistress has a name, it's called Laravel
date: 2012-09-04
tag: frameworks,laravel,php
description: That’s right, I finally gave it a go and spent some time with my new mistress. I only played around with it for a few hours and I’m already blogging
author: Marco Monteiro
categories: [frameworks,laravel,php]
---

That’s right, I finally gave it a go and spent some time with my new mistress. I only played around with it for a few hours and I’m already blogging about it. That’s how cool it is.
Laravel is a clean and classy framework for PHP web development. Freeing you from spaghetti code, Laravel helps you create wonderful applications using simple, expressive syntax. Development should be a creative experience that you enjoy, not something that is painful. Enjoy the fresh air.
<!--more-->
That’s the description you’ll see the first time you get to the Laravel website. And I gotta say, they’re not trying to sell you anything, it is actually like that.

So here are my first impressions on it (be advised, I only spent a few hours with it so far).

**Coming from other frameworks**

You know I use Codeigniter on a daily basis, so I come from a framework that pretty much lets you do anything you like. You can even make your application only with controllers. But, that’s the only thing required for the framework to work. However in Laravel you can use it just with routes, no controllers required. That felt a little weird, I must say.

But that only showed me how powerful the routes actually are in Laravel.

The other thing I still find weird about Laravel is the Manual. The sidebar with parents with closed Childs just doesn’t work for me. I still think Codeigniter has the best Manual out there.

**The things I’m loving so far**

The Template system - Blade.

Well let me tell you, I’m loving this template system. First there’s the name Blade love it. It just works, and look how beautiful it is. 

	@if ( $message == 'success' )
		It was a success!
	@elseif ( $message == 'error' )
		An error occurred.
	@else
		Did it work?
	@endif
	 
	@foreach ($comments as $comment)
		The comment body is {{ $comment->body }}.
	@endforeach

No messy views for you!

**Eloquent ORM**

An ORM is an object-relational mapper, and Laravel has one that you will absolutely love to use. It is named “Eloquent” because it allows you to work with your database objects and relationships using an eloquent and expressive syntax. In general, you will define one Eloquent model for each table in your database. 

Well the manual says it all. In Codeigniter I only used an object-relational mapper one time. I used PhpActiveRecord and it was great, but it was no Eloquent.

Next I’m going to play a bit with bundles, artisan and migrations. I have high expectations for those.

I’m not going into more detail for now specially because I need more time to play with it. But for now, what I can tell you is: Takes a bit to get used to some stuff (coming from another framework, if this is your first php framework you should be ok), and it has some awesomeness built in. 

Loving the experience so far and that’s what really matters in the end of the day, right?