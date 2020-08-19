---
layout: post
title: I would like to express complete and utter disappointment
date: 2013-12-06
tag: funny,shitty job award,Webdev
description: Today we were at the #codeigniter channel on IRC (Freenode). We were discussing who would win the shit job award of the day. I tried to win with a single
author: Marco Monteiro
categories: [funny,shitty job award,Webdev]
---

Today we were at the #codeigniter channel on IRC (Freenode). We were discussing who would win the shit job award of the day. I tried to win with a single file website with CSS, JS, HTML and mySQL in one file. I thought I would win. Well I didn't.

This was Thomas (aka slax0r) submission:

This is an email that he wrote to VPN supplier that one of his clients were using.
<!--more-->

>Hello,

>I would like to express complete and utter disappointment with your company, and your stuff, that you call software.
So, where do I begin, maybe at the start.

>Today I was contacted by a client of ours, who uses your software, more specifically, the VPN server, which I now question my self, why on earth, do they use your software, since there is perfectly good and simple VPN software available, which just *works*, and it's also free, as in beer, and as in speech by the way.

>So to access our clients server, I need a special copy of your VPN client, for which I spent over an hour to even find it on your website. Not to mention how annoying it is to register with an email account, so you can send me all that nice spam, only because I need to download a VPN CLIENT! So after I finally find the correct version, and downloaded it, frustration grows. Might I add I am a Linux user for almost 15 years. So, first thing is first. RAR, for Linux? Seriously? Ever heard of good old GunZip? Or BunZip2? Readilly available on every and *each* Linux distribution. As well as BSD and MacOSX. But ok, I download unrar for Linux, so I could just use your software. So, unrar, unpack the RPM, and install by hand, apply permissions etc. Run the software as a non-privileged user, and whats this. Needs SU permissions? No problem. But your suggestion to make setuid it is beyond idiocracy! Setuid to root? Are you serious? Why don't you just suggest opening up port 22 to the world and removing the root password? Ok then, I just run the app with sudo, and same message, need I say what happened next? Probably not. So ok, after I calmed down a little bit, go to interactive root login through sudo, and run the app. Eureka! It runs. So, insert the VPN data, save configuration, and try to open the connection. Oh snap! Can't read config file. Strange, I'm running as root. Inspect file permissions, hm, all are good, READ/WRITE for root on barracudavpn.conf, but since we already did setuid, what worse can it be if I just make it world readable/writable, right? So ok, make it like that, re-run the application, connect, insert password, and a nice little warning: "Gateway not reachable". Are you kidding me? Inspect interfaces, nothing new, try to ping some VPN IP addresses, nothing, try to ping my own VPN IP address, nothing. Great peace of software, nothing works. But ok, maybe I'm just stupid, so, contact your support. After ALOT of waiting, your "Natalia" comes on, asks me if we own any of your software, well, the VPN client, and nothing else, and I just get blown off, like I am a lesser person, because I don't use your software. Thanks a lot! Mental note: I will never ever use ANY of your software, and anyone I find actually using your stuff, will do my best to convince them other wise.

>Thank you, for making me download Windoze and running it in a VM(that's a Virtual Machine, in case you're wondering), just so I can help out my client. And thank you for making me spend the whole friday on a task that would take me 10-15 minutes.

>Kind regards,
>Thomas

>P.S.: fire your whole Linux dev team, because they CLEARLY have no clue what-so-ever to what they are doing on this system.
>P.S.2: change your website hosting, because your site is working insanely slowly, or optimize it.


Let's just say that this email made my day.

The company in question was this [Barracuda Networks](https://www.barracuda.com/).

**ps: **Thank you slax0r for letting me share this.