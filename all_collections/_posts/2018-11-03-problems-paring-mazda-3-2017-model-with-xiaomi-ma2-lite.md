---
layout: post
title: Problems pairing Mazda 3 2017 model with Xiaomi ma2 Lite
date: 2018-11-03
tag: 2018,android,bluetooth,ma2 lite,mazda 3,xiaomi
description: A few weeks ago I bought me a new phone, the Xiaomi Ma2 Lite. Crazy good phone for the price.
author: Marco Monteiro
categories: [2018,android,bluetooth,ma2 lite,mazda 3,xiaomi]
---

A few weeks ago I bought me a new phone, the Xiaomi Ma2 Lite. Crazy good phone for the price. More on that [here](https://www.youtube.com/watch?v=ZSUWV7yBK8Q). However, I had a small problem with the phone that was actually driving me nuts. I couldn't get it to recognize my car.

<!--more-->

Took me a week to solve this problem, tried almost everything. Soft reset on the phone, soft reset on the car. Hard reset on the phone. I even did a hard reset to the car infotaiment system. But still, my phone could see all my bluetooth devices at home without exeception. But my car? Nope!

Then I came across [this article](https://forum.xda-developers.com/mi-a2-lite/help/mi-a2-lite-bluetooth-wont-pair-car-t3828878) on xda-developers. Basically what worked was this:

1. Enable developer options;
2. Go to Settings > System > Developer Options
3. Enble "Show Bluetooth devices without name"

This way wen you want to connecto to a device you'll be presented with the mac-address and not the device name. This worked like a charm.

