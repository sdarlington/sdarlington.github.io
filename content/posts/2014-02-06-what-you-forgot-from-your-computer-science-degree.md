---
id: 3871
title: 'What you forgot from your Computer Science Degree'
date: '2014-02-06T17:43:47+00:00'
author: 'Stephen Darlington'
excerpt: 'I did a presentation at last nights London iOS Developer Group meeting.'
layout: post
guid: 'http://www.zx81.org.uk/?p=3871'
permalink: /computing/programming/what-you-forgot-from-your-computer-science-degree.html
categories:
    - Programming
tags:
    - benchmark
    - development
    - ios
    - lidg
    - presentation
---

Last night I did a short presentation about my [WSLHTMLEntities](https://github.com/sdarlington/WSLHTMLEntities) open source project at the London iOS Developer Group meeting. You can see the slides here:

<iframe allowfullscreen="" frameborder="0" height="355" loading="lazy" marginheight="0" marginwidth="0" scrolling="no" src="http://www.slideshare.net/slideshow/embed_code/30888583" style="border:1px solid #CCC; border-width:1px 1px 0; margin-bottom:5px; max-width: 100%;" width="425"> </iframe>

<div style="margin-bottom:5px">  **[What you forgot from your Computer Science Degree](https://www.slideshare.net/stephendarlington/what-you-forgot-from-your-computer-science-degree "What you forgot from your Computer Science Degree")**  from **[Stephen Darlington](http://www.slideshare.net/stephendarlington)** </div>Since last time I did a talk there people snickered because I built the slides using PowerPoint, this time I decided to use the latest Apple technology: Keynote in iCloud. Unfortunately this was a bit too new for the Mac Pro they use in the Apple Store, so we ended up downloading a copy in PowerPoint format and loading *that* into the local copy of Keynote. Nothing is ever simple.

One question I got at the end that I was unable to answer is how well it performs compared to other solutions.

This afternoon [I ran a few quick tests](https://github.com/sdarlington/WSLHTMLEntities/tree/benchmark/WSLHTMLEntities).

Firstly I added two further methods of performing the HTML entity replacement:

- [Google Cocoa Toolbox](https://code.google.com/p/google-toolbox-for-mac/)
- Use the new iOS 7 NSAttributedString feature where it can load a HTML document

The last option, while built-in and easy to implement, is not something you’d want to consider if you had any performance requirements. First, it has to run on the main thread. Second, it’s memory footprint is *way* higher than either of the other two solutions. And, finally, it’s slow. In my tests I did a loop of 10,000 iterations. Because of the memory problem I only ran 1000 iterations of the NSAttributedString solution, but it was still about 15 times slower than my version when doing the full 10,000 records (i.e., over 150 times slower overall).

So I’ve not included it in the charts below.

![HTMLEntityChart](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2014/02/HTMLEntityChart-1024x595.png?resize=474%2C275)

I ran eight simple tests with each of the parsers.

There is no clear winner.

As I speculated, WSLHTMLEntities is much more *consistent* than the other two. Google’s varies a lot depending on where in the mapping list the “solution” lies. Replacing &amp;loz; (near the end of the list) takes 50% longer than &amp;amp; (near the beginning) for example.

Still, you’d have to be pretty obsessive to pick one of these solutions for performance reasons alone. Interesting to find out, though!