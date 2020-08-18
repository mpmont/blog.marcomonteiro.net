---
layout: post
title: Glide.js a simple, lightweight & fast jQuery slider
date: 2013-10-22
tag: css3,javascript,jquery,plugin,responsive
description: Glide is responsive and touch-friendly jQuery slider. Based on CSS3 transitions with fallback to older broswers. It's simple, lightweight and fast. Designed to slide, no less, no more. A lot
author: Marco Monteiro
categories: [css3,javascript,jquery,plugin,responsive]
---

Glide is responsive and touch-friendly jQuery slider. Based on CSS3 transitions with fallback to older broswers. It's simple, lightweight and fast. Designed to slide, no less, no more. A lot has been said this past few weeks about OOCSS markup, Jędrzej Chałubek (creator of Glide.js) needed simple and fast slider with fully customizable OOCSS markup. If you're into OOCSS this is the way to go.

<!--more-->

**How to use**

jQuery is the only dependency. Make sure to include it.

	<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
	
Include Glide.js

	<script src="jquery.glide.js"></script>

Link to slider stylesheet inside document head.

	<link rel="stylesheet" type="text/css" href="css/style.css">

Make necessary markup for slider.

	<div class="slider">
		<ul class="slides">
			<li class="slide"></li>
			<li class="slide"></li>
			<li class="slide"></li>
		</ul>
	</div>
  
Init our slider on default options ...

	  <script>
		  $('.slider').glide();
	  </script>
	
**Best features of Glide.js**

* <i class="icon-angle-right"></i> Lightweight ~4,5kB minifed
* <i class="icon-angle-right"></i> Ultra fast CSS3 Transitions
* <i class="icon-angle-right"></i> Responsive
* <i class="icon-angle-right"></i> Touch & mobile friendly
* <i class="icon-angle-right"></i> Public API with callbacks
* <i class="icon-angle-right"></i> OOCSS & BEM
* <i class="icon-angle-right"></i> Swipe event
* <i class="icon-angle-right"></i> Arrows and bullets navigation
* <i class="icon-angle-right"></i> Keyboard navigation
* <i class="icon-angle-right"></i> Autoplay
* <i class="icon-angle-right"></i> Pause on hover

[<i class="icon-link"></i> Glide.js](http://jedrzejchalubek.com/glide/)

[<i class="icon-github"></i> Github](https://github.com/jedrzejchalubek/Glide.js)