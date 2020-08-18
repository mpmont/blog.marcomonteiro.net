---
layout: post
title: Laravel Starter front to back
date: 2013-01-08
tag: books,frameworks,laravel,php
description: I just finished reading this book, so it's now time to give it the review it deserves. First and foremost this is a really small book that you can read
author: Marco Monteiro
categories: [books,frameworks,laravel,php]
---

I just finished reading this book, so it's now time to give it the review it deserves. First and foremost this is a really small book that you can read in hours. However you shouldn't judge a book by its weight. Even though the book is small, it's actually full of useful content.
Like any other book about a framework, it starts by walking the reader into the process of downloading and getting started with the framework. Getting everything ready on all the operating systems.
<!--more-->
The second part of the book walks the reader into making his own web-application. This is when it starts getting interesting. The thing I liked the most about the book is that Shawn didn't focus on the usual subjects. He could've skipped the migrations subject entirely and just give the reader the necessary code to create the users table. But he didn't, he used the migrations and moreover he explains the importance of using migrations while developing web-applications, especially while working with a team.

Another good example of this is when the book gets to the point of using the routing system. Although there are people building entire applications with just routes and not using controllers at all, Shawn takes the time to explain why it’s important to use controllers. This is a very important thing that Shawn keeps saying throughout the book. Laravel is a framework where convention prevails over configuration. This is why I think he chose to explain all of these concepts: you should always follow the conventions while developing with Laravel.

After the chapter where Shawn shows the reader how to build a simple CRUD application, he takes them onto 5 important features that some users of Laravel tend to forget.

**Eloquent relationships**

Here he explains why they are important and most of all how they can save you time. All this while showing examples of how to do it. This is actually a big chapter in the book, and I really think Shawn did a good job explaining all the concepts related to using the built in ORM of Laravel.

**Authentication**

Another feature that some users tend to forget, instead using their own authentication libraries. Here Shawn shows how it is actually a good thing to use the built in authentication.

**Filters**

In this section, Shawn shows the reader how to use filters in Laravel. Note that while he's showing all of this he's always showing examples using the small CRUD application he built in the second chapter of the book. That means the reader gets a pretty good explanation about all this with the help of real life examples.

**Validation**

Validation is actually really important, and here Shawn shows the reader just how important it is. Showing that you can use the validation not only to validate forms, but actually anything in your application. This is great because most people tend to forget that and end up using the validation just for forms.

**Bundles**

The last one is obviously the bundles. Here Shawn shows how you can can make the application modular. And perhaps more importantly, how you can re-use the code. In this chapter he also gives the reader what I think is really good advice.

> The core purpose behind the existence of bundles is code re-use. On the road to mastering Laravel, we recommend implementing new code first without bundles. Then, once you find a need to re-use that code, you may then prefer to bundle the code up and refactor it as necessary. This prevents you from being slowed down by both learning how bundles are put together and by implementing code for the first time in Laravel.

So in case you're wanting to try Laravel and like to start by reading a good book, I definitely recommend this one. It gives you the quick boost you need to create beautiful things with Laravel.