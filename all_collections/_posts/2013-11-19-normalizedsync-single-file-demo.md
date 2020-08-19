---
layout: post
title: normalizedSync.php - Single file demo
date: 2013-11-19
tag: data,database,how-to,sync,tutorial
description: Are you trying to sync de-normalized data from a remote source (e.g. webservice) and struggle importing it into your nicely normalized database? Maybe this little demo might give you an
author: Marco Monteiro
categories: [data,database,how-to,sync,tutorial]
---

Are you trying to sync de-normalized data from a remote source (e.g. webservice) and struggle importing it into your nicely normalized database? Maybe this little demo might give you an idea!

<!--more-->

**Part 1:**  ( [Normalize existing DB-Data](http://sqlfiddle.com/#!2/aa28e/1) )

**Part 2:** Keepin' it all in sync

- run this from your CLI:

		curl -Ls http://git.io/6VTovw | php

- or download the [normalizedSync.php](https://gist.github.com/druu/7541557#file-normalizedsync-php) file and run it locally

**So... just what exactly is going on here?**

**Picture this:**

* <i class="icon-angle-right"></i>  You're facing yourself with the task to frequently pull data from ***theSERVICE*** via their API and keep a synchronized copy on your DB cluster.
* <i class="icon-angle-right"></i>  You skim the docs, run some little test scripts and have soon found just the right combination of URL and request data to get exactly the data you need to have.
* <i class="icon-angle-right"></i>  You head happily and motivated into implementing and testing your little cron jobby.

And then you realize...

**Yeah, but what happened???**

Well... Someone over at ***theSERVICE*** thought:

*"Nah, our users surely won't need the relational data from our systems... Let's give 'em the human friendly, easy readable, flat version."*

Or maybe someone though:

*"3NF - WHAT? Ain't nobody got tyme fo' dat!"*

So basically, you're facing this situation:

 <code><pre>
   +----------------------+---------------------------+--------------------+-------------+
   |  vendor              | category                  | name               |    ....     |
   +----------------------|---------------------------|--------------------|-------------+
   |                      |                           |                    |             |
   |  Vendor 1            | Category 2                | Product 1          |             |
   +-------------------------------------------------------------------------------------+
   |                      |                           |                    |             |
   |  Vendor 1            | Category 2                | Product 2          |             |
   +-------------------------------------------------------------------------------------+
   |                      |                           |                    |             |
   |  Vendor 2            | Category 1                | Product 3          |             |
   +-------------------------------------------------------------------------------------+
   |                      |                           |                    |             |
   |  Vendor 3            | Catefory 3                | Product 4          |             |
   +----------------------+---------------------------+--------------------+-------------+
   \\===> This is the structure of the data you received...
</pre></code>
**But:**

Your system looks like this:

<code><pre>
   +-----+-----------------------+          +-----+--------------------------+
   | id  |  name                 |          | id  |  name                    |
   |-----|-----------------------|          |-----|--------------------------|
   |     |                       |          |     |                          |
   | 1   |  Vendor 1             |          | 1   |  Category 43             |
   +-----------------------------+          +--------------------------------+
   |     |                       |          |     |                          |
   | 2   |  Vendor 2             |          | 2   |  Category 1              |
   +-----------------------------+          +--------------------------------+
   |     |                       |          |     |                          |
   +-----+-----------------------+          +-----+--------------------------+
   \\==============> vendors table          \\==============> categories table
</pre></code>

<code><pre>
   +-----+--------------+-----------------+----------------------+-----------+
   | id  | vendor_id    | category_id     | name                 |    ...    |
   |-----|--------------|-----------------|----------------------|-----------|
   |     |              |                 |                      |           |
   | 1   | 1            | 2               | Product 1            |           |
   +-------------------------------------------------------------------------+
   |     |              |                 |                      |           |
   | 2   | 1            | 3               | Product 2            |           |
   +-------------------------------------------------------------------------+
   |     |              |                 |                      |           |
   | 3   | 2            | 12              | Product OVER 9000    |           |
   +-------------------------------------------------------------------------+
   \\=========================================================> products table
</pre></code>

**And:**

Your cron-script takes an hour to complete...

> Dis no good.

**Enter: This Demo Script!**
Again: just run *"curl -Ls http://git.io/6VTovw | php"* from your CLI and see the data flowing in.

Let me quickly describe what's going on there:

* <i class="icon-angle-right"></i> PHP parses the source file for any class declarations
* <i class="icon-angle-right"></i> The script grabs Jeremy Dorn's (@jdorn) [SqlFormatter](https://github.com/jdorn/sql-formatter) to get some juice ;)
* <i class="icon-angle-right"></i> The main loop is called. Just 3 iterations of a formloop, with constantly growing result sets
* <i class="icon-angle-right"></i> Within the loop:
    * <i class="icon-angle-right"></i> Related data (vendors, categories) get extracted from the flat dataset
    * <i class="icon-angle-right"></i> Then 2 batch insert queries are fired *(ON DUPLICATE KEY UPDATE)* and the results are instantly retrieved
    * <i class="icon-angle-right"></i> And a lookup transformation is applied:
       		 <i class="icon-angle-right"></i> **Before:** *vendors[] = {"id": 1, "name": "Vendor 1"}*
       		 <i class="icon-angle-right"></i> **After:**  *vendors["Vendor 1"] = {"id": 1, "name": "Vendor 1"}*
 	* <i class="icon-angle-right"></i> So with that easy accessible array of meta-infos, for every row of the received data, the columns *vendor* and *category* will be replaced by *vendor_id*, respectively *category_id*
 	* <i class="icon-angle-right"></i> Out of this *normalized* result set, we can quickly create another batch insert
	* <i class="icon-angle-right"></i> And be done.

But seriously, read the source, get a hang of what's happening.  This was more or less hastily done, and probably has loads of things to optimize.

But you get the idea ;)

**One more thing...**

There are a few things I'd like to point out and/or explain:

**Why do you use *array_map()* that much? Why no loops?**

* <i class="icon-angle-right"></i> I easily could've used loops, but I wanted to keep it relatively short.

**Why the hell did you even write this?**

* <i class="icon-angle-right"></i>Well, I started answering a question about how that particular person could implement an efficient way to solve exactly this problem.
* <i class="icon-angle-right"></i> The thing got out of hand...

**So, is it efficient?**

* <i class="icon-angle-right"></i> To be fair, I just lab-tested it. I have no real-life benchmarks or anything.
* <i class="icon-angle-right"></i> This particular thing uses 15 db queries in total, and the queries aren't super complex either. But again, I have not analyzed in regards of performance

**Okay, Lab-tested? You sure have run it against a DB, haven't ya?**

***OK! Here's the interesting bit:***

We've got 3 classes (Sorry @jdorn ):

* <i class="icon-angle-right"></i> Helper
* <i class="icon-angle-right"></i> Extractor
* <i class="icon-angle-right"></i> DB


It is *Helper's* job to simulate the API-call, perform the lookup transformations, generate the query string, and so on. Just a little collection of sort of generic methods.

When you run the script you will see some output like

<code><pre>
*** SysStats: *******************************************************
	$> Received 918 products!
	$> DB Stats:
	$> COUNT(vendors.*) : 100 rows
	$> COUNT(categories.*) : 100 rows
	$> COUNT(products.*) : 1867 rows
	$> Current query count: 15
*** End of SysStats *************************************************
</pre></code>

When you take a look at *Helper::get_products()* you will find that I've limited the number of unique vendors and categories to a hundred results each.  That's just for the sake of creating key-collision so the update part of the query is fired to, demonstrating the desired behaviour. (Albeit only accumulating data at this point)

Then we've got the *Extractor* *(cue dramatic music)*
It's whole purpose is just to extract the meta-info from the API's data, induce the assembly of the query string, and initiate the lookup optimization.

> ...sigh.

Yeah, and then there's the weird uncle at the family reunion, that no one is sure of his actual relation to your family. He also stinks, and doesn't like you.

**Ladies and gentlemen, please welcome: the *Database*-Emulator!**

I can't quite explain what led my to produce this piece of... this thing. But hey! It does it's job!

It emulates an **extremely** reduced subset of a DBMS, taking an actual SQL-Query, extracting the wanted data from it, and storing it in a projection of what should've been some sort of Relational DBMS scheme.

Also, not wanting to overcomplicate it too much, I just gave it a few quick'n'dirty shorthand methods, to make it obey. :)

As I said, check the source! It's always fun to see, what the human brain comes up with, when you're actually drifting into insanity. :D

Drop me a note, if I haven't scared you already :)

**And just btw:**
[Here's a call graph.](http://i.imgur.com/JRWcbfC.png)
And [here's the Gist](https://gist.github.com/druu/7541557)

> Have Fun!
> druu

**P.S.:** Thanks to Jeremy Dorn (@jdorn) for that supreme SQL Formatter and to Marco Monteiro for editing and publishing this bit :) You rock! \o/