---
layout: post
title: My Sublime text 3 config
date: 2017-02-02
tag: sublime, sublime-text
description: For the last 4 years or so I've been using sublime text 2. I bought the license, therefore I saw no point in upgrading. Until today, when I found out
author: Marco Monteiro
categories: [sublime text, sublime]
---

For the last 4 years or so I've been using sublime text 2. I bought the license, therefore I saw no point in upgrading. Until today, when I found out that I could use my ST2 license on ST3 (beta). Today was configuration day and I re-configured editor or choice.

<!--more-->

**Packages**

**[Package Control](https://packagecontrol.io)**

The Sublime Text package manager that makes it exceedingly simple to find, install and keep packages up-to-date.

**[BracketHighligher](https://packagecontrol.io/packages/BracketHighlighter)**

Bracket Highlighter matches a variety of brackets such as: [], (), {}, "", '', #!xml <tag></tag>, and even custom brackets.

This was originally forked from pyparadigm's SublimeBrackets and SublimeTagmatcher (both are no longer available). I forked this to fix some issues I had and to add some features I had wanted. I also wanted to improve the efficiency of the matching.

**[Codeigniter Snippets](https://packagecontrol.io/packages/CodeIgniter%20Snippets)**

A list of codeigniter snippets for Sublime Text 2. If you use Codeigniter this is a must have.

**[DocBlockr](https://packagecontrol.io/packages/DocBlockr)**

DocBlockr is a package for Sublime Text 2 & 3 which makes writing documentation a breeze. DocBlockr supports JavaScript (including ES6), PHP, ActionScript, Haxe, CoffeeScript, TypeScript, Java, Apex, Groovy, Objective C, C, C++ and Rust.

**[Emmet](https://packagecontrol.io/packages/Emmet)**

Emmet is a plugin for many popular text editors which greatly improves HTML & CSS workflow:

**[Git](https://packagecontrol.io/packages/Git)**

https://packagecontrol.io/packages/Git

**[GitGutter](https://packagecontrol.io/packages/GitGutter)**

A Sublime Text 2/3 plugin to see git diff in gutter

**[PhpDoc](https://packagecontrol.io/packages/PhpDoc)**

PhpDoc support package.

**[SideBarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements)**

Provides enhancements to the operations on Sidebar of Files and Folders for Sublime Text. http://www.sublimetext.com/ Notably provides delete as “move to trash”, open with.. and a clipboard. Close, move, open and restore buffers affected by a rename/move command. (even on folders)


**[SublimeLinter](https://packagecontrol.io/packages/SublimeLinter)**

Interactive code linting framework for Sublime Text 3


**[SublimeLinter-php](https://packagecontrol.io/packages/SublimeLinter-php)**

SublimeLinter 3 plugin for PHP, using php -l.

**[DocPHP](https://packagecontrol.io/packages/DocPHPManualer)**

Show the document of current function on Sublime Text.

**[Material Theme](https://packagecontrol.io/packages/Material%20Theme)**

Material Theme, the most epic theme for Sublime Text 3 by Mattia Astorino


**[Statusbar Path](https://packagecontrol.io/packages/Statusbar%20Path)**

Since I use Sublime in fullscreen most of the time its really usefull to have the complete path of the file I'm working on on the status bar.

**[PHPfmt](https://packagecontrol.io/packages/phpfmt)**

This one is essential so you dont have to worry about your indentation in php.

Here's my config:

    {
	"enable_auto_align": false,
	"indent_with_space": true,
	"passes":
	[
		"ConvertOpenTagWithEcho",
		"PrettyPrintDocBlocks",
		"ReturnNull",
		"OnlyOrderUseClauses"
	],
	"psr1": false,
	"psr2": true,
	"version": 2
	}


**And finally my config file:**

    {
	  "auto_complete_commit_on_tab": false,
	  "bold_folder_labels": true,
	  "caret_style": "phase",
	  "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
	  "detect_indentation": false,
	  "draw_white_space": "all",
	  "fallback_encoding": "UTF-8",
	  "file_exclude_patterns":
	  [
		  "*.pyc",
		  "*.pyo",
		  "*.exe",
		  "*.dll",
		  "*.obj",
		  "*.o",
		  "*.a",
		  "*.lib",
		  "*.so",
		  "*.dylib",
		  "*.ncb",
		  "*.sdf",
		  "*.suo",
		  "*.pdb",
		  "*.idb",
		  ".DS_Store",
		  "*.class",
		  "*.psd",
		  "*.db"
	  ],
	  "folder_exclude_patterns":
	  [
		  ".svn",
		  ".hg",
		  "CVS",
		  ".hgcheck"
	  ],
	  "font_face": "M+ 1mn light",
	  "font_size": 14,
	  "highlight_line": true,
	  "highlight_modified_tabs": true,
	  "ignored_packages":
	  [
		  "Vintage"
	  ],
	  "line_padding_bottom": 1,
	  "line_padding_top": 2,
	  "match_brackets": true,
	  "match_brackets_angle": true,
	  "match_brackets_braces": true,
	  "match_brackets_content": true,
	  "match_brackets_square": true,
	  "rulers":
	  [
		  80,
		  120
	  ],
	  "scroll_past_end": true,
	  "show_full_path": true,
	  "tab_size": 4,
	  "tabs_small": true,
	  "theme": "Material-Theme.sublime-theme",
	  "translate_tabs_to_spaces": true,
	  "trim_trailing_white_space_on_save": true,
	  "vintage_ctrl_keys": true,
	  "vintage_start_in_command_mode": false,
	  "word_wrap": true
	}

**Keybindings**

	[
    	{ "keys": ["ctrl+shift+left"], "command": "next_view_in_stack" },
    	{ "keys": ["ctrl+shift+right"], "command": "prev_view_in_stack" },
    	{ "keys": ["alt+d"], "command": "goto_definition" },
    	{ "keys": ["ctrl+7"], "command": "toggle_comment", "args": { "block": false } },
    	{ "keys": ["ctrl+shift+7"], "command": "toggle_comment", "args": { "block": true } }
	]

This way if you don't need to click to use the goto definition functionality.

If you want to use the same font I use you can find it [here](http://www.fontspace.com/m-fonts/m-1mn) on some ocasions I also use [M+ 2m](http://www.fontspace.com/search/?q=M%2B+2m). One other thing I also like to change is the application icon. At home I use [this one](https://dribbble.com/shots/2289001-Sublime-Text-Icon-Replacement).

If you really want to go nuts about it you can also add a icon package thing so all your icon files are specific to the type of file you have open. Some themes have that, some don't. To solve that just use [this repo here](https://github.com/mrmartineau/SetiUI-Icons-Sublime) and follow all the instructions.