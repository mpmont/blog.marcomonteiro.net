---
layout: post
title: How to get started with Docker part 1 - Installing Docker
date: 2019-01-13
tag: 2019,containers,docker,linux,ubuntu
description: Yes, I know! Everyone has been using docker for the last few years but I'm late on that hype train. At work we're still using vagrant like assholes, that's my
author: Marco Monteiro
categories: [2019,containers,docker,linux,ubuntu]
---

Yes, I know! Everyone has been using docker for the last few years but I'm late on that hype train. At work we're still using vagrant like assholes, that's my own fault really. I decided to dip my dick into that docker pool and blog the entire process. Here's the first part.

<!--more-->

I'm using Ubuntu now. So the docs for it is right [here](https://docs.docker.com/install/linux/docker-ce/ubuntu/).

**1. Uninstall old versions**

Older versions of Docker were called docker or docker-engine. If these are installed, uninstall them:

	$ sudo apt-get remove docker docker-engine docker.io containerd runc

**2. Setup the repository**

Update the apt package index:

	$ sudo apt-get update

Install packages to allow apt to use a repository over HTTPS:

    $ sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common

Add Docker’s official GPG key:

	$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint.

    $ sudo apt-key fingerprint 0EBFCD88

    pub   4096R/0EBFCD88 2017-02-22
          Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    uid                  Docker Release (CE deb) <docker@docker.com>
    sub   4096R/F273FCD8 2017-02-22

Use the following command to set up the stable repository. You always need the stable repository, even if you want to install builds from the edge or test repositories as well. To add the edge or test repository, add the word edge or test (or both) after the word stable in the commands below.

Note: The lsb_release -cs sub-command below returns the name of your Ubuntu distribution, such as xenial. Sometimes, in a distribution like Linux Mint, you might need to change $(lsb_release -cs) to your parent Ubuntu distribution. For example, if you are using Linux Mint Rafaela, you could use trusty.

    $ sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"


**3. Install Docker CE**

Update the apt package index.

	$ sudo apt-get update

Install the latest version of Docker CE, or go to the next step to install a specific version:

	$ sudo apt-get install docker-ce

Now, let's just test if everything is working as it should.

Verify that Docker CE is installed correctly by running the hello-world image.

	$ sudo docker container run hello-world

This should be your output.

    Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    1b930d010525: Pull complete
    Digest: sha256:2557e3c07ed1e38f26e389462d03ed943586f744621577a99efb77324b0fe535
    Status: Downloaded newer image for hello-world:latest

    Hello from Docker!
    This message shows that your installation appears to be working correctly.

    To generate this message, Docker took the following steps:

	 1. The Docker client contacted the Docker daemon.
     2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
     3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
     4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
     $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
     https://hub.docker.com/

    For more examples and ideas, visit:
     https://docs.docker.com/get-started/

On the next article we're going to look into installing Docker compose.

[Docker documentation](https://docs.docker.com/) for reference.