---
id: 720
title: 'Growing Up in Public'
date: '2008-12-02T20:10:46+00:00'
author: 'Stephen Darlington'
excerpt: 'What do Britney Spears and Yummy, my iPhone application, have in common? If you had asked me a few months ago I would have said nothing but I''d have been wrong. No, they both have had to grow up in public.'
layout: post
guid: 'http://www.zx81.org.uk/?p=720'
permalink: /computing/opinion/growing-up-in-public.html
categories:
    - Opinion
tags:
    - apple
    - Computing
    - development
    - iphone
    - Software
---

What do Britney Spears and [Yummy](http://www.yummyapp.com/), my iPhone Delicious.com client, have in common? If you had asked me a few months ago I would have said nothing but I’d have been wrong. No, they both have had to grow up in public.

For a version [1.0](http://www.yummyapp.com/2008/09/yummy-10-now-available-from-app-store.html) product, Yummy seemed solid to me. It was fast, coped will all my bookmarks and had the ability to add, edit and delete entries. I didn’t think that this would remain as a unique feature for as long as it has, but hey, that’s a bonus.

Within a few days I had exceeded what I had expected to sell and received positive feedback on the iTunes store. But not long after that I also received my first bug report.

This turned out to be an odd one. It crashed early on while starting up and downloading all the bookmarks for the first time. My first guess — incorrect as it turned out — was that it was running out of memory. It took some investigation with the help of a very kind end-user to discover that… Delicious allows technically invalid URLs. By that I mean both that they don’t follow web standards and, worse, that it’s not even possible to open them in Mobile Safari.

I don’t feel so bad about not spotting that one during testing, although I should have put in more error handling to spot various “impossible” events and make sure that it didn’t crash. The reason I mention it is to give an idea of the kind of things that happen in “real life.”

But my biggest mistake has been assuming that I am a typical user of Delicious. I thought a few hundred bookmarks was a lot but I now realise that I was wrong. I have some users with over a thousand bookmarks and have read about another with nearly ten times that ((I confess to being a little sceptical about some claims. At some points it becomes a bit of a pissing competition.)).

The exact number of bookmarks that you can store depends on a number of variables, such as the length of the URL, title and notes, the number of tags, the iPhone operating system ((Upgrading from version 2.0 to 2.1 tipped at least one user over the edge, and many developers do not get previews of new versions.)) and a bunch of other details outside my control. Looking at the reviews on iTunes I believe a few people had more than whatever that limit is. Unfortunately the error handling was lacking, resulting in Yummy crashing rather than an inconvenient but understandable error message ((I’ve not got to the bottom of this one yet. It seems that, sometimes, you can only spot a bad memory allocation by noting that an otherwise mandatory field is missing.)).

[Version 1.0.2](http://www.yummyapp.com/2008/10/yummy-version-102.html) was actually a big release in terms of the amount of code changed, if not in terms of visible functionality (which is why it was such a small change in the version number). Under the hood, though, I dramatically increased the number of bookmarks that Yummy could handle. However it was starting to become clear that the internal architecture was holding me back. Further increasing the number of usable bookmarks would be hard, if not impossible, without seriously degrading performance and some new features that I wanted to add would end up in a nasty tangle of unmaintainable code.

I decided to take a step back and fix the structure of the code. For much of the time since the last formal release, Yummy has been, metaphorically speaking, in pieces on the floor. Most of those pieces have now been polished and reassembled, and it’s now working well enough that I have replaced the copy of 1.0.2 that I have been using day-to-day on my own iPhone with the development version.

This is a long way of saying that there is a new version coming. There will be a number of great new features but many of the big changes are behind the scenes. I sincerely hope that you don’t notice them.