---
title: 'Migrating to FreshRDD'
date: '2025-08-22T10:49:53+01:00'
author: 'Stephen Darlington'
excerpt: 'Migrating to FreshRDD'
layout: post
categories:
    - Opinion
tags:
    - computing
    - opinion
    - web
---
I’ve gone through a number of RSS clients over the years. I used to be a big Google Reader user. I used Reeder on my iPad a lot, and now I use [NetNewsWire](https://netnewswire.com). To ensure that my feeds are shared between devices, I’ve used [Feedly](https://www.feedly.com). I’ve paid for it, as I use it a lot and I don’t want it to go away like Google Reader did.

But they keep adding stuff that I have no interest in, including jumping on the AI bandwagon. It has, however, been fast and reliable. I don’t have much to complain about.

But there’s always some new toy to play around with, and I decided I wanted to play around with a self-hosted aggregator. [FreshRSS](https://freshrss.org/) works with NetNewsWire, it has a good feature set, and, by web app standards, is pretty easy to install.

There were a few non-obvious points, though, so I thought I would share a few notes.

The obviously problem with self-hosting is that you need somewhere to host it! Firing up an EC2 instance, even a small one, could easily end up costing more than an annual subscription to Feedly. I always have a bunch of Raspberry Pi’s floating around, but how would I access them when I’m out of the house?

VPNs are all well and good, but they’re often fussy or fragile or difficult to maintain, or require cooperation from your WiFi router. I don’t have the patience. However, there is another option: [Tailscale](https://www.tailscale.com). It’s like a VPN mesh, allowing your various devices to talk to one another. I add the client to my Pi 5, iPad and iPhone, and they can all connect with known host names wherever they are.

[Installation](https://freshrss.github.io/FreshRSS/en/admins/03_Installation.html) is pretty simple. The tricky part is adding the right software to the Pi’s OS, but the installation page tells you exactly what it can and cannot find. Once the right dependencies are installed, it ran first time.

The next trick: access to the API -- which is how NetNewsWire communicates with it -- is disabled by default. You need to play around with the settings to get going.

And finally, the big gotcha. If you follow all the instructions and import your feeds, you’ll get a fully functional system. But, it will never automatically refresh your feeds! (There’s a Refresh button in the web UI, but if, like me, you always use it from an app, it will quickly get stale.) The steps _are_ [documented](https://freshrss.github.io/FreshRSS/en/admins/08_FeedUpdates.html) but is a challenge if you’re not expecting to look for them!

And that’s it. I now have an operational, self-hosted instance of FreshRSS. My Feedly subscription still has a few months left, so I’m not decided whether to switch fully, but it’s nice to have the option.
