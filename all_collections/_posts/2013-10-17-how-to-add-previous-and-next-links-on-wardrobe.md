---
layout: post
title: How to add Previous and Next links on wardrobe
date: 2013-10-17
tag: laravel,laravel 4,tips,wardrobe
description: If you're a regular here you may have noticed that I'm always making some small improvements on my blog. The last one was quite simple, I just wanted to add
author: Marco Monteiro
categories: [laravel,laravel 4,tips,wardrobe]
---

If you're a regular here you may have noticed that I'm always making some small improvements on my blog. The last one was quite simple, I just wanted to add some previous and next links when the user is reading an article. However, I wasn't aiming to just simple arrows. I wanted to user to see the title of those articles.

Since my blog uses wardrobe and that is built on top of Laravel, doing that is pretty straight forward.

<!--more-->

First let's go to the PostController and get those articles.

This is the function you're looking for:

	/**
	 * Display the specified resource.
	 *
	 * @param string $slug
	 *
	 * @return Response
	 */
	public function getShow($slug)
	{
		$post = $this->posts->findBySlug($slug);
		if ( ! $post)
		{
			return App::abort(404, 'Page not found');
		}

		return View::make('themes.'.$this->theme.'.post', compact('post'));
	}

So let's get the prev and next articles based on the Post object.

	/**
	 * Display the specified resource.
	 *
	 * @param string $slug
	 *
	 * @return Response
	 */
	public function getShow($slug)
	{
		$post = $this->posts->findBySlug($slug);
		if ( ! $post)
		{
			return App::abort(404, 'Page not found');
		}
		$prev = DB::table('posts')->orderBy('id', 'asc')->where('id', '>', $post->id)->where('active', '1')->first();
		$next = DB::table('posts')->orderBy('id', 'desc')->where('id', '<', $post->id)->where('active', '1')->first();

		return View::make('themes.'.$this->theme.'.post', compact('post', 'next', 'prev'));
	}

Quite easy right? Now you may want to do the same in your getPreview function.

	/**
	 * Show a post preview.
	 *
	 * @param int $id
	 *
	 * @return Response
	 */
	public function getPreview($id)
	{
		$post = $this->posts->find($id);
		if ( ! Auth::check() or ! $post)
		{
			return App::abort(404, 'Page not found');
		}
		$prev = DB::table('posts')->orderBy('id', 'asc')->where('id', '>', $post->id)->where('active', '1')->first();
		$next = DB::table('posts')->orderBy('id', 'desc')->where('id', '<', $post->id)->where('active', '1')->first();

		return View::make('themes.'.$this->theme.'.post', compact('post', 'next', 'prev'));
	}

Now you just need to add that navigation links to your layout. I added mine to my post.blade.php file, since our next and prev links will only be used there.

	<nav class="other_posts">
		<ul>
			@if($next)
				<li id="next"><a href="{{ url('post/'.$next->slug) }}" rel="prev">{{ $next->title }} </a></li>
			@endif
			@if($prev)
				<li id="previous"><a href="{{ url('post/'.$prev->slug) }}" rel="next">{{ $prev->title }}</a></li>
			@endif
		</ul>
	</nav>

That's is, nice and easy.

**ps:** Soon after I published this post I had [this talk](https://twitter.com/marcogmonteiro/status/390842895458369536) with [Dan Horrigan](https://twitter.com/dhrrgn). Turns out there's a better way to do it.

Basically he got the same result with just one query. Look at this beauty.

  	public function getShow($slug)
  	{
	  	$post = $this->posts->findBySlug($slug);
	  	if ( ! $post)
	  	{
		  	return App::abort(404, 'Page not found');
	  	}

	  	$posts = DB::select('SELECT * FROM `posts` WHERE `active` = 1 AND (`id` = (SELECT MIN(`id`) FROM `posts` where `id` > ?) OR `id` = (SELECT MAX(`id`) FROM `posts` where `id` < ?))', array($post->id, $post->id));

	  	$prev = null;
	  	$next = null;
	  	$count = count($posts);
	  	if ($count == 2) {
		 	list($prev, $next) = $posts;
	  	} elseif ($count == 1) {
		  	if ($posts[0]->id > $post->id) {
			  	$next = $posts[0];
		  	} else {
			  	$prev = $posts[0];
		  	}
	  	}

	  return View::make('themes.'.$this->theme.'.post', compact('post', 'next', 'prev'));
  	}

Keep in mind that this is really only useful if it is a high traffic site. Thank you [Dan](https://twitter.com/dhrrgn).