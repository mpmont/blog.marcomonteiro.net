---











So we version our code, and we obviously use git. BUt what if you wanted something to happen every-time we do make an action.

Well git-hooks got you covered. 

<!--more-->

The current definition of git hooks:

> Hooks are little scripts you can place in $GIT_DIR/hooks directory to trigger action at certain points. When git init is run, a handful of example hooks are copied into the hooks directory of the new repository, but by default they are all disabled. To enable a hook, rename it by removing its .sample suffix.
 
> <small>**Note:** It is also a requirement for a given hook to be executable. However - in a freshly initialized repository - the .sample files are executable by default.</small>

I'm not going to mention all the "actions" you can use with git-hooks. You can RTFM for that.

However, I can give you a real life example. 

Imagine you're using less with javascript:

	<link rel="stylesheet/less" type="text/css" href="css/styles.less" />
	<script src="js/lib/less-1.1.3.min.js" type="text/javascript"></script>
	
But now you want that to compiled every time you done editing and commit/push to your development server and the git post-recieve hook runs your build.sh and builds your css adn all that malarkey.

> **Post-receive**

> This hook is invoked by git-receive-pack on the remote repository, which happens when a git push is done on a local repository. It executes on the remote repository once after all the refs have been updated.

> This hook executes once for the receive operation. It takes no arguments, but gets the same information as the pre-receive hook does on its standard input.

> This hook does not affect the outcome of git-receive-pack, as it is called after the real work is done.

[<i class="icon-link"></i> RTFM](http://git-scm.com/docs/githooks)

[<i class="icon-youtube-play"></i> Net-Tuts tutorial on git-hooks](http://net.tutsplus.com/tutorials/tools-and-tips/quick-tip-automation-with-git-hooks/)