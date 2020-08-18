---
layout: post
title: Start using CLI more and more with mycli
date: 2018-07-18
tag: 2018,linux,mysql,ubuntu
description: Ever since I moved into Linux I started using the CLI even more. Don't get me wrong, I used it quite a lot on Mac. However if there was one
author: Marco Monteiro
categories: [2018,linux,mysql,ubuntu]
---

Ever since I moved into Linux I started using the CLI even more. Don't get me wrong, I used it quite a lot on Mac. However if there was one thing that I normally didn't use it for was for mySQL. However a few days ago I discovered [mycli](http://www.mycli.net/). Since then I gotta say. Love it!

<!--more-->

Here's a bit more about the tool.

Install the thing first:

    $ sudo apt-get install mycli

**Usage:**

    $ mycli --help
	Usage: mycli [OPTIONS] [DATABASE]
  	A MySQL terminal client with auto-completion and syntax highlighting.

  	Examples:
    	- mycli my_database
    	- mycli -u my_user -h my_host.com my_database
    	- mycli mysql://my_user@my_host.com:3306/my_database

	Options:
  		-h, --host TEXT               Host address of the database.
  		-P, --port INTEGER            Port number to use for connection. Honors $MYSQL_TCP_PORT.
  		-u, --user TEXT               User name to connect to the database.
  		-S, --socket TEXT             The socket file to use for connection.
  		-p, --password TEXT           Password to connect to the database.
  		--pass TEXT                   Password to connect to the database.
  		--ssl-ca PATH                 CA file in PEM format.
  		--ssl-capath TEXT             CA directory.
  		--ssl-cert PATH               X509 cert in PEM format.
	  	--ssl-key PATH                X509 key in PEM format.
	  	--ssl-cipher TEXT             SSL cipher to use.
  		--ssl-verify-server-cert      Verify server's "Common Name" in its cert against hostname used when connecting. This option is disabled by default.
		-V, --version                 Output mycli's version.
		-v, --verbose                 Verbose output.
		-D, --database TEXT           Database to use.
		-d, --dsn TEXT                Use DSN configured into the [alias_dsn] section of myclirc file.
		--list-dsn                    list of DSN configured into the [alias_dsn] section of myclirc file.
		-R, --prompt TEXT             Prompt format (Default: "\t \u@\h:\d> ").
		-l, --logfile FILENAME        Log every query and its results to a file.
		--defaults-group-suffix TEXT  Read MySQL config groups with the specified suffix.
		--defaults-file PATH          Only read MySQL options from the given file.
		--myclirc PATH                Location of myclirc file.
		--auto-vertical-output        Automatically switch to vertical output mode if the result is wider than the terminal width.
		-t, --table                   Display batch output in table format.
		--csv                         Display batch output in CSV format.
		--warn / --no-warn            Warn before running a destructive query.
		--local-infile BOOLEAN        Enable/disable LOAD DATA LOCAL INFILE.
		--login-path TEXT             Read this path from the login file.
		-e, --execute TEXT            Execute command and quit.
		--help                        Show this message and exit.


![Example](https://raw.githubusercontent.com/dbcli/mycli/master/screenshots/tables.png)

![Example 2](https://raw.githubusercontent.com/dbcli/mycli/master/screenshots/main.gif)


**Features**

[mycli](http://www.mycli.net/) is written using [prompt_toolkit](https://github.com/jonathanslenders/python-prompt-toolkit/).

* <i class="icon-angle-right"></i> Auto-completion as you type for SQL keywords as well as tables, views and columns in the database.
* <i class="icon-angle-right"></i> Syntax highlighting using Pygments.
* <i class="icon-angle-right"></i> Smart-completion (enabled by default) will suggest context-sensitive completion.
* <i class="icon-angle-right"></i> SELECT * FROM <tab> will only show table names.
* <i class="icon-angle-right"></i> SELECT * FROM users WHERE <tab> will only show column names.
* <i class="icon-angle-right"></i> Support for multiline queries.
* <i class="icon-angle-right"></i> Favorite queries with optional positional parameters. Save a query using \fs alias query and execute it with \f alias whenever you need.
* <i class="icon-angle-right"></i> Timing of sql statments and table rendering.
* <i class="icon-angle-right"></i> Config file is automatically created at ~/.myclirc at first launch.
* <i class="icon-angle-right"></i> Log every query and its results to a file (disabled by default).
* <i class="icon-angle-right"></i> Pretty prints tabular data (with colors!)
* <i class="icon-angle-right"></i> Support for SSL connections
