---
layout: post
title: Getting started with Docker part 2 - Install Docker Compose
date: 2019-01-15
tag: 2019,docker,linux
description: You can run Compose on macOS, Windows, and 64-bit Linux. Docker Compose relies on Docker Engine for any meaningful work, so make sure you have Docker Engine installed either locally
author: Marco Monteiro
categories: [2019,docker,linux]
---

You can run Compose on macOS, Windows, and 64-bit Linux.

Docker Compose relies on Docker Engine for any meaningful work, so make sure you have Docker Engine installed either locally or remote, depending on your setup.

On Linux systems, first install the Docker for your OS as described on the Get Docker page, then come back here for instructions on installing Compose on Linux systems.

<!--more-->

To run Compose as a non-root user, see [Manage Docker as a non-root user](https://docs.docker.com/install/linux/linux-postinstall/).

On Linux, you can download the Docker Compose binary from the Compose repository release page on GitHub. Follow the instructions from the link, which involve running the curl command in your terminal to download the binaries. These step by step instructions are also included below.

Run this command to download the latest version of Docker Compose:

    sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Apply executable permissions to the binary:

	sudo chmod +x /usr/local/bin/docker-compose

Optionally, install command completion for the bash and zsh shell.

I use zsh so here's what to do:

Place the completion script in your /path/to/zsh/completion (typically ~/.zsh/completion/):

	mkdir -p ~/.zsh/completion
	$ curl -L https://raw.githubusercontent.com/docker/compose/1.23.2/contrib/completion/zsh/_docker-compose > ~/.zsh/completion/_docker-compose

Include the directory in your $fpath by adding in ~/.zshrc:

	fpath=(~/.zsh/completion $fpath)

Make sure compinit is loaded or do it by adding in ~/.zshrc:

	autoload -Uz compinit && compinit -i

Then reload your shell:

	exec $SHELL -l

**Available completions**

Depending on what you typed on the command line so far, it completes:

**Available docker-compose commands**

* - Options that are available for a particular command
* - Service names that make sense in a given context, such as services with running or stopped instances or services based on images vs. services based on Dockerfiles. For docker-compose scale, completed service names automatically have “=” appended.
* - Arguments for selected options. For example, docker-compose kill -s completes some signals like SIGHUP and SIGUSR1.
* - Enjoy working with Compose faster and with fewer typos!


**Test the installation.**

	$ docker-compose --version
	docker-compose version 1.23.2, build 1110ad01

[Docker documentation](https://docs.docker.com/) for reference.