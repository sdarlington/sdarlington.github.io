---
id: 522
title: 'Byline Bypass?'
date: '2008-07-15T21:29:52+01:00'
author: 'Stephen Darlington'
excerpt: 'Just as you can''t judge a book by its cover, you can''t always judge an application only by its user interface.'
layout: post
guid: 'http://www.zx81.org.uk/?p=522'
aliases: ['/computing/opinion/byline-bypass.html']
categories:
    - Opinion
tags:
    - apple
    - development
    - iphone
    - Software
---

Earlier today [daringfireball pointed me](http://daringfireball.net/linked/2008/07/15/byline) to [Byline](http://www.phantomfish.com/byline.html) by Phantom Fish, a Google Reader client-side application for the iPhone.

Since I recently abandoned Safari’s built-in RSS reader for [Google](http://www.google.com/reader/), this is just the kind of application that I have been looking for. Unlike a lot of programs I’ve found on the AppStore, Byline seems to be very well put together. The author appears to have included a thoughtful set of features. Not *everything*, just those elements you use every day; either a good starting point for later versions or an Apple-like approach depending on your perspective.

However, one thing worries me: Google have not released a publicly available API for Reader. Unless Phantom Fish have reached some deal with Google — and there’s nothing on their website to say that they have — then the only way that this application can work is if they reverse engineered the protocol[^1].

I’m confident that the interface works now, but what about tomorrow? The popular opinion is that Google are [not happy with parts of the API](http://code.google.com/p/pyrfeed/wiki/GoogleReaderAPI) and will [publish the full version soon](http://www.niallkennedy.com/blog/2005/12/google-reader-api.html), but until the API is publicly available and stable there are no guarantees and it could change at any time.

Do you want to spend ?5.99 on an application that could be disabled at any time by a third party? As useful as it looks to be, I don’t want to start relying on an application with foundations as shaky as this.
[^1]: My first thought was that it was just a specialised RSS feed. However, the video shows support for the “Star” functionality and they say that it synchronises read status, etc.
