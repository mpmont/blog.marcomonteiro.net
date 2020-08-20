Last week i explained how to structure a good signature on your code and why. This week i’ll be explaining how i do my css coding and how i structure my files. First of all i’d like to point you to some useful websites that can help you get started coding with css.
Ok now the next part and i’ll try to keep it clean and simple.
<!--more-->
First, how to divide my document? Well i do it the same way every single time. Top to bottom. So let’s imagine that your site is going to have this sections:

Header / Navigation / Sidebar / Content / Footer

the division will be this exact same order. So the first thing i like to do is create something that let me know where i am when i’m scrolling trough my css file.

For example i always create something like this:

	/* --------------------------------------------------------------
	HEADER
	* ALL THE HEADER STYLES. (includes search and breadcrumbs)
	-------------------------------------------------------------- */

This simple division can help you and someone that is working with you to know where to put new code and to look for something. This division is big enough to highlight from the rest of the document and if you add information like (includes search and breadcumbs) that will help a lot because the header will probably have some other small stuff inside so it is a best practice to always do this.

Remember always code in a way that other developer can continue your job, because your job is never finished.

With that in mind you can begin your coding and there is some other point that i still have to mention in this article, always be specific and i say that for everything in your code. Some developers have some trouble naming stuff and they might call a navigation bar just a menu and that’s ok, but why not go beyond that and say horizontal-menu or even main navigation? you know, a website can have more than one menu and if you call it just “menu” what are you going to call the second menu? second-menu? i don’t think that is a good idea.

With this in mind there’s one more thing where you have to be really specific: and that is the way you declare your classes and id’s in your file. One thing that you probably do quite a lot is something like this:


	.header{
		background: #000;
	}

i’m sorry to say but for me this is wrong. The reason is really simple, when you look at that code can you tell me the markup that is using that class? No, you can’t! So why not declare the markup on your css like this:

	div.header{
		background: #000;
	}

This tell me much more, now i know that the header will be a div. This small changes to your way of coding can be very useful to you and to your fellow developers.

Of corse for a rulle like this there’s always an exception, if you use a class to more than one markup element than you can use the first example.

On another matter on more thing i see a lot is code that does the exact same thing repeated over and over. This is really annoying. Imagine something like this:
You are going to use a color for all the text on your site, and every-time you need it you declare a new class. Does that make any sense? Obviously not! So please try not to do it and reutilize your code.

So what should you retain on this post:
1 - Always structure your files Top to Bottom;
2 - Always be specific with your naming and coding;
3 - Don’t repeat yourself;
4 - Reutilize your code;