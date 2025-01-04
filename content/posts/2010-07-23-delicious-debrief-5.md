---
id: 2155
title: 'Delicious Debrief (Part 5/5)'
date: '2010-07-23T20:26:21+01:00'
author: 'Stephen Darlington'
excerpt: 'Developing iPhone software isn''t all sex, drugs and rock and roll. Sometime you have to make difficult changes because of things outside your control. Here is part five of my story from late last year.'
layout: post
guid: 'http://www.zx81.org.uk/?p=2155'
permalink: /computing/opinion/delicious-debrief-5.html
adman_disable:
    - 'on'
categories:
    - Opinion
tags:
    - apple
    - development
    - iphone
    - Opinion
    - rant
    - yahoo
---

### The story so far

Last year Yahoo! announced, with no notice, a significant change that had far reaching consequences for all third party applications including my iPhone program, Yummy. This is the third in a series of posts that discusses how I dealt with it.

We’ve already talked about most of the work, starting with an [overview](http://www.zx81.org.uk/computing/opinion/delicious-debrief.html), [the announcement, the low level technical challenges](http://www.zx81.org.uk/computing/opinion/delicious-debrief-2.html) and the implementation ([technical](http://www.zx81.org.uk/computing/opinion/delicious-debrief-3.html) and [UI](http://www.zx81.org.uk/computing/opinion/delicious-debrief-4.html)). All that remains it to launch it, and that’s what we’re going to talk about today.

### Availability

I switched my own Delicious account over to use my Yahoo! ID to shake out as many bugs as possible and I’d already had a few emails from people asking if they could help, so by the time I submitted the update to Apple it was in pretty good shape.

It launched on 13 December 2009, simultaneously for the full version and Yummy Browser. I decided against holding back for the free version.

Despite the volume of code that had changed, I decided to call is a “point” update (moving from version 2.3.1 to 2.3.2) because it didn’t really add any new user-level features. In hindsight maybe I should have made more of a fuss over it, since it was the first — and is still the only — Delicious iPhone app that supported Yahoo! IDs. But it felt wrong to kick my competitors over something that was just as outside their control as mine ((Six months later and with no updates from any of them I’m feeling less charitable!)).

### Lessons

So what have we learned through all this process?

I’ve learned how vulnerable Yummy is to outside influence. I had been planning a new feature release before the end of last year but this slipped until the first quarter of 2010 because of all the work that I have outlined above. I’m glad that I’ve kept “agile” (an overused word in the software industry), sticking to relatively small and frequent releases as this made it much easier to change from one feauture set (mostly what you see in the current Yummy 2.4 release) to another (OAuth).

But I think most of the lessons need to be taken on the other side, by Yahoo! From my point of view there were multiple failures:

1. No notice. It was impossible to have an application ready for day zero as we just didn’t know that a change was coming
2. No documentation. Even when we found out about the change there was little to no documentation about how to make the change
3. No concessions to desktop apps. It just is not possible to write a desktop application ((By “desktop” I mean something that doesn’t run in a web browser. iPhone apps in this sense are “desktop” applications.)) with a fluid, easy to use UI. OAuth works nicely for web apps but not so well for desktop (and mobile) ones. Twitter is pushing forward with xAuth which solves this problem. It’s not yet standardised, which is a problem, but guaranteeing a poor user experience is hardly a winning strategy either
4. No transition. When Twitter moved from basic auth to OAuth ((Past tense as, while this process is still ongoing, it will be complete shortly.)), both systems worked for over a year. This meant that there was no single, big switch over. True, they incentivised new apps to use the new scheme and the end of basic auth is going to orphan a bunch of apps but, still, there has been a year when developers can transition from one scheme to the other. For Delicious this change happened overnight, but not for all users. Instead we have to support both schemes and with no obvious method of knowing which one to use in advance

Luckily Yahoo! seem to have noticed the pain that their development community have been put through. They have since (albeit very recently) tried to get a handle on who is developing what against their APIs. Quite how they’ll use that information is anyones guess but it’s certainly a step in the right direction.