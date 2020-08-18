---
layout: post
title: Codeigniter Pagination - Re-use query strings
date: 2012-08-23
tag: codeigniter,pagination
description: A few months ago I had a problem. I was paginating some results based on some data the user had provided. So I needed to be able to pass that
author: Marco Monteiro
categories: [codeigniter,pagination]
---

A few months ago I had a problem. I was paginating some results based on some data the user had provided. So I needed to be able to pass that data from page to page during the pagination process. First I set to read the Codeigniter documentation to see if it was possible to do that with the pagination library. 

Turns out I could if I set up that data to be a query string and save it in my suffix param. However this solution had a problem. Every-time the user clicked the first or last link on the pagination the query string would disappear. 
<!--more-->
So I searched some more, and found something even better. The new version of the pagination Library (3.0) already had that feature. So if you ever need it and don’t want to wait for the next version of Codeigniter you just have to do the following. 

Download the version 3.0 of the Pagination Library [here](https://github.com/EllisLab/CodeIgniter/blob/develop/system/libraries/Pagination.php).

Extend your current version of the pagination Library with the one that you just downloaded. (see how to do that [here](http://codeigniter.com/user_guide/general/core_classes.html))

As you can see the pagination now has one more param than before. It’s called reuse_query_string. And just by setting that to TRUE, you can now use both uri segments and query strings in your pagination.

    protected $base_url			= ''; // The page we are linking to
	protected $prefix			= ''; // A custom prefix added to the path.
	protected $suffix			= ''; // A custom suffix added to the path.
	protected $total_rows			= 0; // Total number of items (database results)
	protected $per_page			= 10; // Max number of items you want shown per page
	protected $num_links			= 2; // Number of "digit" links to show before/after the currently viewed page
	protected $cur_page			= 0; // The current page being viewed
	protected $use_page_numbers		= FALSE; // Use page number for segment instead of offset
	protected $first_link			= '&lsaquo; First';
	protected $next_link			= '&gt;';
	protected $prev_link			= '&lt;';
	protected $last_link			= 'Last &rsaquo;';
	protected $uri_segment			= 3;
	protected $full_tag_open		= '';
	protected $full_tag_close		= '';
	protected $first_tag_open		= '';
	protected $first_tag_close		= '&nbsp;';
	protected $last_tag_open		= '&nbsp;';
	protected $last_tag_close		= '';
	protected $first_url			= ''; // Alternative URL for the First Page.
	protected $cur_tag_open			= '&nbsp;<strong>';
	protected $cur_tag_close		= '</strong>';
	protected $next_tag_open		= '&nbsp;';
	protected $next_tag_close		= '&nbsp;';
	protected $prev_tag_open		= '&nbsp;';
	protected $prev_tag_close		= '';
	protected $num_tag_open			= '&nbsp;';
	protected $num_tag_close		= '';
	protected $page_query_string	= FALSE;
	protected $query_string_segment 	= 'per_page';
	protected $display_pages		= TRUE;
	protected $_attributes			= '';
	protected $_link_types			= array();
	protected $reuse_query_string           = FALSE;
	protected $data_page_attr		= 'data-ci-pagination-page';    