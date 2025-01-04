---
id: 49
title: 'Bored of constant tweaking?'
date: '2004-02-24T22:48:33+00:00'
author: 'Stephen Darlington'
excerpt: 'Frustrations with wireless networking and Linux. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/opinion/bored-of-constant-tweaking.html'
permalink: /computing/opinion/linuxrant.html
categories:
    - Opinion
tags:
    - Computing
    - fun
    - Linux
    - mac
    - Opinion
    - unix
    - wifi
---

**Introduction**

This page is just a rant, a way for me to vent my anger. Don’t expect it to be fully rational or for it to make perfect sense. It could, even, be my excuse for buying new hardware; I do like my gadgets.

In fact, this piece is going to be an anti-Linux rant. If you’ve seen the rest of my website this may surprise you. I have, after all, been using Linux since 1994 when I installed Slackware from a knee-high pile of 3.5 inch floppy-discs. I spent a year writing “[The Penguin Says](/computing/linux/tps/)“, a collection of Linux application reviews, I have the [Oracle 8i Installation HOWTO](/computing/oracle/oracle-howto/) in the [Linux Documentation Project](http://www.tldp.org/). I’m no fly-by-night, recent Linux convert.

So my rant really starts when I moved house near the end of last year. My flats topography means that the phone point (and, hence, ADSL router) is at the opposite side of the place to my spare room and desktop PC. The choice was to try to stretch an Ethernet cable from one side of the flat to the other or to add a wireless card to my computer. How hard could it be?

**Tricky**

Very hard, it turns out.

I picked a cheap WiFi card, which may have been a mistake, but it did have Open Source drivers written by the manufacturer. That, I thought, was a good sign.

In practise it kind of work sometimes and it does stutter at times. No fun when you’re trying to [listen to music](/computing/opinion/slimp3.html). In some sense, if it didn’t work at all I’d be less annoyed. But it *nearly* works and you can’t count on it.

**Installation**

The driver comes in source format along with a utility to configure it. I’m running Fedora Core 1 which has a fairly heavily patched kernel, but luckily it still built with no errors. It picked the “standard” version of gcc rather than 3.2 (which you should use to build the kernel) but that was easily fixed. The configuration tool is also easily built if you have the Qt development libraries installed. It’s at this point that things go wrong.

On next boot, Fedora recognises the new network interface and generates a configuration file for eth1. Unfortunately the driver thinks of the device as ra0 so the OS just gets confused and fails to start the network.

Anyway, to cut a very long and boring story short(er), you need to define the WEP keys, network name and so-forth in the Qt GUI. It appears not to work anywhere else, even though Fedora comes with “standard” tools that should really do the job.

But even then the network doesn’t start when you boot. Instead you start the machine, let the initialisation fail, log into X, unload the device driver using the supplied script, load it in again and then start the Qt configuration tool. The network is now (usually) up and will work for two or three hours before causing a kernel panic.

**Conclusion**

I’m not really sure what I’m railing against here. It could be my new flat. It could be my old PC. It could be my cheap and cheerful WiFi card. Or its driver. Or the general standard of WiFi support in Linux. And perhaps it’s just because I’ve been spoiled with my iBook and its “just works” wireless networking.

I don’t have any solutions and I don’t really have the money for new kit, much as I’d like one of those G5’s!.

So I’m not sure if you got anything out of reading this, but I think I got something out of writing it! If you’re seeing the same frustrations — and if you have any solutions! — let me know on the discussion forums.