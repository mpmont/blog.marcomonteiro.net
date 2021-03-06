I’m just getting started with Composer. I’ve been reading a lot about it and I think it’s the way to go. I don’t know many common developers (like me) that are already using it, but I’m going to give it a go. No more Git articles for you. From now on the two main subjects on my blog will be Composer and Unit Testing, since I decided that’s what I’m going to do next.
What is this thing called Composer?

Composer is a tool for dependency management in PHP. It allows you to declare the dependent libraries your project needs and it will install them in your project for you.
<!--more-->
**How does that work?**

Well it’s quite easy. All there is to know actually is that there’s two logical parts involved:

* The repository: where all your packages will be stored.
* The command line utility: that will help you manage everything.
* To install Composer first you have to navigate to your project.

		$ cd /path/to/my/project

Then you download Composer into your project

		$ curl -s http://getcomposer.org/installer | php

Well, the first time I tried this I ran into a little trouble. I always got the following message:

Some settings on your machine make Composer unable to work properly. Make sure that you fix the issues listed below and run this script again:

The detect_unicode setting must be disabled.

Add the following to the end of your `php.ini`:

	detect_unicode = Off

If you’re not using the native PHP that comes with your system (I’m assuming you’re using a unix based system) and you’re using something like Mamp, Mamp Pro or even Zend Server you probably need to edit your php.ini file to add that line. However, you must check if the path to your php.ini is correct. In my case I had one of those apps installed and it was checking for the native php.ini path.

To check this, run the following:

		$ php -i | grep ini

Then you can update the correct php.ini. Moving forward.

At this point you should have a file called composer.phar in your project root. That is your command line utility. You can check if everything is ok by running the following command:

		$ php composer.phar

That will give you all the available commands.

That’s it, that is all you need to know about installing composer into your projects. In the next issue we’ll talk about getting actual packages from http://packagist.org/ and working with them in your projects.

For now, browse the following websites:

* [GetComposer](http://getcomposer.org/)
* [Packagist](http://packagist.org/)