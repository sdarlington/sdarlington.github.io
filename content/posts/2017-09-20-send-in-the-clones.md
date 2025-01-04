---
id: 4687
title: 'Send in the clones!'
date: '2017-09-20T20:24:44+01:00'
author: 'Stephen Darlington'
excerpt: 'Help! My backups are too efficient!'
layout: post
guid: 'https://www.zx81.org.uk/?p=4687'
aliases: ['/blog/send-in-the-clones.html']
categories:
    - Blog
tags:
    - apple
    - backblaze
    - help
    - superduper
    - support
    - 'time machine'
---

<iframe allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" frameborder="0" height="281" loading="lazy" referrerpolicy="strict-origin-when-cross-origin" src="https://www.youtube.com/embed/HDbxzdbvGhU?feature=oembed" title="Frau Farbissina: Send In The CLONE!" width="500"></iframe>

So here’s the thing that drives me crazy.

Having had a hard disk die on me a few years ago, I’m a little paranoid about backups. I have three:

1. [Time Machine](https://en.wikipedia.org/wiki/Time_Machine_(macOS)), over WiFi to a [Synology NAS](https://www.synology.com/en-uk/products/series/j)
2. [Backblaze](https://www.backblaze.com), “cloud” backup over the internet
3. [SuperDuper](http://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html) clone to an infrequently connected USB hard disk

Time Machine and Backblaze run all the time, nice, seamless and hopefully pretty complete. I do the SuperDuper clone occasionally and every few months I try to reboot and check that the clone actually works.

And that’s where the problems start.

If I forget to turn off WiFi — which I almost always do — then when the clone starts up, it immediately connects to WiFi and starts to back up to Time Machine. I panic and stop it as soon as I realise.

But then I boot back to my main disk and… Time Machine decides it needs to do a *full* backup. Which. Takes. Forever. (Backblaze is also doing a huge backup, presumably for the same reason.)

What’s the answer to this? Is there a way to switch off WiFi on the clone automatically? Only start when the boot disk has a specific name? I don’t know! It’s hard to search for because I can’t think what the answer might be.