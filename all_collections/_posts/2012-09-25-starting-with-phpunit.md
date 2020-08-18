---
layout: post
title: Starting with PHPUnit
date: 2012-09-25
tag: composer,php,php-unit,TDD,tests
description: Last week I told you all about my next set of articles on my blog. My main focus will be PHPUnit and Composer. Not because I’m an expert about the
author: Marco Monteiro
categories: [composer,php,php-unit,TDD,tests]
---

Last week I told you all about my next set of articles on my blog. My main focus will be PHPUnit and Composer. Not because I’m an expert about the subject, but for the exact opposite â€” I’m learning as I go.
Let’s define “the thing” first.

PHPUnit is the de-facto standard for unit testing in PHP projects. It provides both a framework that makes the writing of tests easy as well as the functionality to easily run the tests and analyse their results.

That take us to another subject. Test Driven Development or TDD. 
<!--more-->

**What is TDD?**

Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes an (initially failing) automated test case that defines a desired improvement or new function, then produces the minimum amount of code to pass that test and finally refactors the new code to acceptable standards.

Since last week I showed you how to get started with Composer now is quite easy to install PHPUnit framework into your projects.

This is how my composer.json looked like last week.

	{
    	"require": {
        	"kriswallsmith/assetic": "*"
    	}
	}

Until recently there was no official PHPUnit package listed at packagist.org, essentially because the author used PEAR and he didn’t believe in the Composer project. However, now we have a official package at Composer.

**Installing PHPUnit**

First navigate to your project folder and then edit your composer.json file.

	{
		"require": {
			"kriswallsmith/assetic": "*",
			"phpunit/phpunit": "3.7.1"
		}
  	}

Since 3.7.1 was the lastest stable release when I wrote this, that’s the version I went with. After editing your composer.json file you just have to run your update Composer command. To do so, in your terminal run:

	$ php composer update

**This will be the result:**

  	Loading composer repositories with package information
  	Updating dependencies
	- Installing symfony/yaml (v2.1.2)
	  Downloading: 100%         
  
	- Installing phpunit/php-text-template (1.1.2)
	  Downloading: 100%         
  
	- Installing phpunit/phpunit-mock-objects (1.2.0)
	  Downloading: 100%         
  
	- Installing phpunit/php-timer (1.0.3)
	  Downloading: 100%         
  
	- Installing phpunit/php-token-stream (1.1.4)
	  Downloading: 100%         
  
	- Installing phpunit/php-file-iterator (1.3.2)
	  Downloading: 100%         
  
	- Installing phpunit/php-code-coverage (1.2.2)
	  Downloading: 100%         
  
	- Installing phpunit/phpunit (3.7.1)
	  Downloading: 100%
	  
As you can see, Composer is already working for us installing everything it’s needed to work with PHPUnit.

This is all there is to know about installing PHPUnit into your projects. On the next issue I’m going to tell you all about the TDD process and after that we’re going to actually start using PHPUnit in a small PHP project.