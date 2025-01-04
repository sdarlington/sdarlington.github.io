---
id: 1930
title: 'Delicious Debrief (Part 1/5)'
date: '2010-07-19T20:13:11+01:00'
author: 'Stephen Darlington'
excerpt: 'Developing iPhone software isn''t all sex, drugs and rock and roll. Sometime you have to make difficult changes because of things outside your control. Here is part one of my story from late last year.'
layout: post
guid: 'http://www.zx81.org.uk/?p=1930'
permalink: /computing/opinion/delicious-debrief-part-15.html
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

### Background

For the benefit of any new visitors, I develop an iPhone application called [Yummy](http://www.yummyapp.com/) that connects to the [Delicious.com](http://delicious.com/) “social bookmarking” website, allowing you to access and share your bookmarks using a far more usable interface than the native web or mobile optimised version of the site.

In the olden days — that is more than six months ago — to access Delicious all you had to do was enter a user name and password. As a developer it was very similar. Whenever you wanted to access something that required authorisation — adding a new bookmark for example — you had to supply the same credentials as you would on the web: a username and password. This, in web terminology, is called “basic authentication.”

And then in October last year, Yahoo! announced that any new accounts would be linked to their Yahoo! ID, the same username and password that are used to protect Yahoo! Mail, Flickr and most other Yahoo! services. A month later they allowed existing users to transition their old account to the new Yahoo! ID world.

On the Delicious.com website things look very similar. You still enter a username and password and can then access protected resources. But for developers things work a bit differently.

In the rest of this series of posts I’d like to talk about this transition and the difficulties involved. In the six months that it’s taken me to get around to writing this I’ve calmed down a lot but I’m sure you’ll be able to feel the frustration I felt at some points.

I’m going to split the discussion into a number of different “chapters.” First there’s how Yahoo! dealt with the transition. Next are the technical challenges, the options I tried and, eventually, the solution I settled on.

What follows is not densely technical, in the sense that I’m not going to be talking to the level of individual lines of code. However many of the decisions and trade-offs are somewhat technical in nature. Most people should be able to follow the process if not every last detail.

[Tomorrow we’ll start with the announcement](http://www.zx81.org.uk/computing/opinion/delicious-debrief-2.html) and why what they changed made things tricky for all third-party clients, including Yummy.