---
layout: post
title: Protecting your home network from ads and some telemetry
date: 2021-02-21
tag: linux, raspberrypi, security, ads, telemetry, piHole
description: Recently I&#39;ve been very interested in this project called Pi-hole. Where you can basically filter all the requests your devices do in your network and just block some undesired behaviours that can occur in your network.
author: Marco Monteiro
categories: [ linux, raspberrypi, security, ads, telemetry, piHole ]
---
Recently I&#39;ve been very interested in this project called Pi-hole. Where you can basically filter all the requests your devices do in your network and just block some undesired behaviours that can occur in your network.

<!--more-->

With Pi-hole you&#39;ll get this set of features:

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Network-wide protection</u></strong></h3>

Instead of browser plugins or other software on each computer, install Pi-hole in one place and your entire network is protected.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Block in-app advertisements</u></strong></h3>

Network-level blocking allows you to block ads in non-traditional places such as mobile apps and smart TVs, regardless of hardware or OS.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Improve network performance</u></strong></h3>

Since advertisements are blocked before they are downloaded, network performance is improved and will feel faster.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Monitor statistics</u></strong></h3>

Our Web interface offers control of your Pi-hole and a central place to view statistics. We also include an API for extending these stats. I wanted to re-utilize an old Raspberry Pi version 3 I had laying around that I haven’t used in a long time so here&#39;s the process. First, you&#39;ll need a Pi, a zero could work fine just make sure you have that, a case, a power brick and an SD card.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Setup the Raspberry Pi</u></strong></h3>

Head on to the Pi [website](https://www.raspberrypi.org/software/operating-systems/#raspberry-pi-os-32-bit) and download the latest version of the Pi software. You don&#39;t need a desktop environment for this so the lite version should suffice. Then you can use any tool to flash your SD card. Since I&#39;m on Linux I used [Balena Etcher](https://www.balena.io/etcher/) way easier than using dd. After this you want to open the boot folder in your SD card and create an empty file called SSH and we&#39;re ready to start.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Update your system</u></strong></h3>

Insert your SD card into your Pi and boot it up. Then you&#39;ll need to find your Pi IP address in your network. You can easily find this on your router. Once you&#39;ve done that open up your terminal and access your Pi via SSH.

    $ ssh pi@youripaddresshere

This will ask you for a password and that will be raspberry by default. After this you might want to change the default password.

    $ passwd

Then enter your old password and your new password 2 times. To update your system just do the following:

    $ sudo apt update && sudo apt upgrade

This might take a while. Once it&#39;s done you might need to check if you have curl installed and if not, install it.

    $ sudo apt install curl

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Install the Pi-hole software</u></strong></h3>

Here we take the easier route. One-Step Automated Install those who want to get started quickly and conveniently may install Pi-hole using the following command:

    curl -sSL https://install.pi-hole.net | bash

During the process of install you&#39;ll be asked a bunch of question, but my process was very straight forward. Just say yes to all the default options and you&#39;ll be fine. Once the process is complete, you&#39;ll be presented with your Pi-hole password. Make sure to save that somewhere. You can now access your Pi-hole admin panel by just typing the IP address of your pi in your browser.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Setup your Pi-hole so it can be used in your entire network</u></strong></h3>

There&#39;s two ways you can use the Pi-hole. You can use it in a per device choice. This way you basically should only go into the router to make sure your Pi always uses the same IP. The best way you can use the Pi-hole is to setup the system to be used by all the devices in your network, and that&#39;s what I did. To do that the next steps are different on every router so you might need to do some googling at this point, but here&#39;s what I have and what I did.

Setup the IPv4 and IPv6 static IP. In my case these are my settings, you can find yours in your information tab on your Pi-hole admin panel.

192.168.1.2 and 2001:818:xxxx::192:168:1:2 in my case.

<h3 style="font-weight: 400; font-size: 26px;"><strong><u>Huawei HS8247W (Smart Router 2) (Specific to my router)</u></strong></h3>

**Step 1** Advanced settings -&gt; LAN -&gt; DHCP Settings Primary DNS Server: 192.168.1.2

**Step 2** Advanced Settings -&gt; IPv6 -&gt; DHCPv6 Server DNS LAN administrative origin: Static config Preffered DNS: 2001:818:xxxx::192:168:1:2

**Step 3** Advanced Settings -&gt; WAN Config -&gt; DNS Server configuration IPv4 / Origin: Personalized Primary DNS: 1.1.1.1 Secondary DNS: 1.0.0.1

**Step 4** Advanced Settings -&gt; WAN Config -&gt; DNS IPv6 Server configuration / Origin: Personalized / Primary DNS: 2606:4700:4700::1111 / Secondary DNS: 2606:4700:4700::1001

That&#39;s it, now always leave your Raspberry Pi on and you&#39;ll be fine. If your internet connection goes out for some reason, just make sure your cat didn&#39;t disconnect the Pi.