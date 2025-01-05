---
id: 2327
title: 'Giving Back'
date: '2010-10-05T19:04:38+01:00'
author: 'Stephen Darlington'
excerpt: 'Returning the changes I made to some open source projects back upstream.'
layout: post
guid: 'http://www.zx81.org.uk/?p=2327'
aliases: ['/computing/software/giving-back.html']
adman_disable:
    - 'on'
categories:
    - Software
tags:
    - code
    - coding
    - development
    - iphone
    - opensource
---

A few years ago I was very much “into” the whole open source movement. I read LWN (still do, actually). I bought a copy of The Cathedral and the Bazaar.

But one thing I never really did was contribute to open source projects. I never really had much need. They largely did what I wanted and when they didn’t, well, the modifications were too big to consider attempting in my spare time.

And now I have a couple of applications in Apple’s App Store. I get the impression that a lot of apps you see there these days are mainly collections of open source code bundled together with some glue code and some new graphics. I know it sounds bad when you phrase it like that, but I don’t mean it that way. When you’re coding to a deadline and to cost this is a perfectly valid way of doing things.

But neither Yummy nor www.cut are like that. They are almost entirely my own code. Why? Two main reasons.

The first is historical: Yummy was initially developed when the now infamous NDA was in place. Developers couldn’t share code even if they wanted to.

Secondly, I like to minimise external dependencies. The iOS platform changes fast enough as it is without having to wait for other developers to update code as well. Of course, open source means that I could fix it myself but that probably means looking at code I’m not completely familiar with and that takes time. The desire to remove third party code led me to remove AdMob in Yummy Browser and www.cut and replace with Apple’s iAd, even knowing that the fill rate was very low[^1].

Ultimately, however, there’s too much great code out there to avoid it altogether. The current, shipping version of Yummy has two open source components and I have just released a (tiny) third one.

First is the Facebook Connect SDK. I have not made any modifications to this.

Second is InAppSettingsKit. This some software that duplicates the Settings screen and allows them to be included within the app as well as in the Settings.app. I made some minor fixes so that it works on the iPad (independently fixed and pushed upstream) and I added a “Log in to Facebook” cell. I’m not sure how common a requirement this is likely to be, so I’ve not pushed it back to the maintainers but I have made it available in a separate branch:

[InAppSettingsKit](http://github.com/sdarlington/InAppSettingsKit)

Third is something that should really be included in iOS itself. Apple’s guidelines say that when your app is sent into the background it should close any menus that are open. In “iPhone Speak” these are called UIAlertView (dialog in the middle of the screen) and UIActionSheet (menu from the bottom of the screen).

In addition, the iPad had a further requirement: there should be only one menu open at any given time.

I created UIViewAutoDismiss to help:

[UIViewAutoDismiss](http://github.com/sdarlington/UIViewAutoDismiss)

This code is inspired by a [question and answer on Stackoverflow](http://stackoverflow.com/questions/3105974/dismissing-UIAlertViewAutoDismisss-when-entering-background-state).
[^1]: Early indications are that, even with the lower fill rate, income is not vastly different, and this is with only two countries active at the moment with iAds.
