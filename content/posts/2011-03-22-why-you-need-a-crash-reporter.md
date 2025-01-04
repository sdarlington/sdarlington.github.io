---
id: 2758
title: 'Why you need a crash reporter'
date: '2011-03-22T20:02:22+00:00'
author: 'Stephen Darlington'
excerpt: 'If you write iOS software and are waiting for crash reports to be delivered to iTunes Connect, you''re doing it wrong.'
layout: post
guid: 'http://www.zx81.org.uk/?p=2758'
aliases: ['/computing/opinion/why-you-need-a-crash-reporter.html']
image:
    - ''
embed:
    - ''
seo_follow:
    - 'false'
adman_disable:
    - 'on'
categories:
    - Opinion
tags:
    - apple
    - appstore
    - development
    - ipad
    - iphone
    - Software
---

Most developers of iOS applications have a love-hate relationship with the main interface with Apple.

No, let me re-phrase that.

Most developers of iOS applications hate iTunes Connect, the main impediment to a good relationship with Apple.

To be fair it has improved since it opened in mid-2008. One of those improvements has been the inclusion of crash reports. A crash report, in case you’re not a developer, is something that iOS devices such as iPhones and iPads write out when an application crashes. It includes all kinds of useful information, including some, but not all, of the internal state of the application in question. It’s very, very useful for diagnosing problems.

However, what has become clear is that not all of the crash reports make it into iTunes Connect. There are two, maybe three, levels of screening going on. First, the user has to sync their phone with iTunes. I do this mainly to update my podcasts but otherwise I’d do it fairly infrequently. Second, the user also needs to allow the crash reports to be uploaded. I suspect most users do but, you never can tell. Third, Apple clearly does… *something* with the reports when it gets them. There’s clearly some degree of filtering going on but quite what is anyones guess.

The practical upshot of all this is that you’re quite likely to hear about crashes before you see them. I’ve seen reviews in iTunes complain about crashes. I’ve received tweets and support emails. And all before a single report appears in iTunes Connect.

It’s the reviews in iTunes that bug me the most, as I have no way to ask for further information.

Until now.

The most recent version of Yummy, Yummy Browser and www.cut all included [crash reporting code](https://github.com/TheRealKerni/QuincyKit). That is, should the app crash, the next time it’s launched it will say as much as offer to upload the report to a web server.

As I type this I see around a hundred crash reports on my web-server and zero in iTunes Connect. Luckily, I’ve seen no bad reviews in iTunes and, surprisingly, I’ve had no support emails or queries on Twitter.

Without the crash reporter I would have had no idea there were these serious bugs — I’d never seen them! I’m always surprised about crashing bugs as I consider myself to be the main user and so likely to come across these problems first.

Using the reports I can easily see that 90% of the crashes were coming from two bugs. Interesting but slightly less importantly, I can also see that jailbroken phones seem to have more problems than others. I see that the vast majority of my users are on 4.x, with 4.2.1, by far, being the most common. (None of the bugs are OS specific so these numbers should be pretty representative.)

The other thing about having the details on a web-server is that I was able to flag them. When a crash with a known fix is submitted, the apps will now tell the user that this is the case.

I never thought I’d say that the lack of support email is a bad thing, yet there was one bug that took me a long time to track down. I could see where exactly in the code it was crashing but I could see no way that it could actually happen. In the end I stumbled across it quite by chance, but being able to talk to a user who was experiencing the problem would, in this case, have been very useful.

No software is perfect. But at least now I can see problems almost as soon as they happen and provide direct and timely feedback. This is such a huge plus that it shouldn’t be underestimated.