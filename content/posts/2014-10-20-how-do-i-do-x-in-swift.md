---
id: 4128
title: 'How do I do "X" in Swift?'
date: '2014-10-20T20:43:42+01:00'
author: 'Stephen Darlington'
excerpt: 'Maybe I can save you some time reading blogs about Swift...'
layout: post
guid: 'http://www.zx81.org.uk/?p=4128'
aliases: ['/computing/opinion/how-do-i-do-x-in-swift.html']
categories:
    - Opinion
---

Maybe I have some duff feeds in my RSS reader. Maybe I have a few poor choices of people that I follow on Twitter. But I see links along these lines all the time:

> How do you do *something* in Swift?

The answer is, almost always, *exactly the same way you’d do it in Objective-C!*

You want to do pull-to-refresh? Same.

You want to play with location services? Same.

You want to display one of the new UIAlertControllers? That’s the same, too.

Why? Because they’re all part of the underlying framework, the framework that’s there whichever language you’re using. That includes both Apple-languages — Swift and Objective-C — and everything else, C#, Python, Ruby.

That’s not to say that there is nothing useful to write about Swift. As a new language there are lots of things to write about, new ways of structuring your code, better ways of implementing algorithms. Tricks to avoid common errors or pitfalls. But interfacing with the OS? The syntax changes slightly but the code is pretty much the same.