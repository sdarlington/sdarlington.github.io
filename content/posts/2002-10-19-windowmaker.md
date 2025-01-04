---
id: 128
title: 'WindowMaker 0.20.0'
date: '2002-10-19T17:22:55+01:00'
author: 'Stephen Darlington'
excerpt: 'Stephen Darlington finds that there is a window manager that looks good, is easy to use and is fully featured. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/linux/tps/windowmaker-0200.html'
aliases: ['/computing/linux/tps/windowmaker.html']
categories:
    - 'The Penguin Says'
tags:
    - Linux
    - Opinion
    - review
    - Software
    - unix
---

**Introduction**

I remember when I was at school I sometimes got bad grades when writing essays. This, the teachers claimed, was because I’d used an unconventional structure. Rather than start with an introduction, continue with the discussion and finish with my conclusion I’d often start with a rather long introduction, which included my view, and then argued my case in the rest of the text. I guess it weakened my argument a little to do it like that, but people did remember it!

I’ve still not learned my lesson. One of the first things I do with the review — not quite an essay but along the same lines — is say that I think that WindowMaker is the best window manager that I’ve used. In fact I like it so much I’m seriously considering changing from AfterStep, the window manager that I’ve used practically since I had a PC that could support X.

**What’s so good?**

Superficially WindowMaker is not that different to AfterStep. That could be part of the reason I liked it so much. (And after my [disappointing experience with the new version of AfterStep](as14.html) last week I was most definitely open to suggestion.) Just like AfterStep and the NeXT, WindowMaker has a dock, or a wharf or whatever you want to call it, down the right hand side of the screen. This time there is also a paper-clip icon in the top left of the screen. This is WindowMaker’s method of moving between its virtual desktops. It’s a lot less fiddly than AfterStep’s mini-map but only slightly less intuitive.

Windows are handled in, more or less, the same way as AfterStep, they even look similar. The title bar is nicely gradiated, the top left has the minimise button, the top right has the close gadget. At the bottom of the window is the resize bar. A nice touch is the ‘technical drawing’ lines that are used to show where and how big the new window will be. It’s good to know that an *xterm* is eighty characters wide.

So far we’ve found that WindowMaker and AfterStep are pretty much the same. It’s when you try and configure things that the differences appear. To add an icon to the AfterStep dock you must open a text configuration file and try and interpret the syntax. Not *hugely* difficult, but someone used to Microsoft Windows isn’t going to be too happy. The WindowMaker method: open the application you want to dock; drag one of the icons, the one without the title at the top, to the dock. That’s it.

Unless you’re just skim-reading, you should have found something odd with the last paragraph, even if you ignore my English: “…drag *one of* the icons…” An explanation is in order here. WindowMaker does not just have an icon to indicate that an application has been minimised. If you launched a program any way other than from the dock then you get an extra icon, just as if you’d minimised the window but without a title at the top. Until I figured what it was for I was incredibly confused! The first one *is* the application — use it as you would in any other window manager. The other can be dragged to a dock. It’s a waste of screen real-estate and I can’t help but think that there must be a better way of doing it.

Other configuration parameters are also handled graphically in WindowMaker. Try to change some of the colours, or the backdrop or any other parameter in AfterStep and it’s back to the configuration file. WindowMaker has a very nice WindowMaker Preferences Utility to allow you to change them all graphically. I’ve not had the need to dig into the GNUstep directory yet it’s so complete.

**The Verdict**

If you don’t know that I’m impressed then you just haven’t been paying attention(!). While there are faster and smaller window managers, WindowMaker is small and fast *enough*. It is also very simple to use — it’s one of the first free window managers that doesn’t insist that you edit large and complex configuration files — looks superb and is fully functional.

And finally, despite dire warnings that it’s still beta software, it seems to be more stable than many commercial applications. (I only had one glitch: I loaded Netscape once and WindowMaker vanished and *twm* took its place. I have no idea what happened there!)