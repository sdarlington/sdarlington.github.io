---
id: 57
title: 'Random Changes'
date: '2006-01-07T12:42:24+00:00'
author: 'Stephen Darlington'
excerpt: 'When annoyance leads to certain revelations about software engineering truisms. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/opinion/random-changes.html'
aliases: ['/computing/opinion/randomchanges.html']
categories:
    - Opinion
tags:
    - computer science
    - Computing
    - Opinion
    - Programming
    - Software
---

When it first happened I was irritated. A few days later I was irritated that I was still irritated. It didn’t make any sense, it wasn’t a big thing and it shouldn’t have bugged me at all, much less still a few days later.

After a while I realised that my irritation was more rational than I initially thought so I started to write them down as a way of structuring them. And here they are.

So what went wrong? Well, first we’ll need a little background, although I’m sure you will appreciate that I can’t go into all the details.

My day-job involves writing code, enhancing and fixing a sprawling, ten year old application and this day was no different. For the previous few weeks I had been developing a small improvement to one of the reports. I had satisfied the requirements by modifying an existing report, including the occasional conditional where appropriate. Not my best piece of work by any means but I had spent some time on it, had some of myself invested in it in some small way. I checked in the change to our source control system and moved on to other things. A short while later someone reported a bug against it. Not an unusual occurrence with the very vague requirements I was working to and the general standard of my code, however one thing did surprise me — I was sure that I’d tested for and added code for that particular scenario.

It turns out that I was right. The problem was that somebody had completely rewritten my code. The new implementation was very elegant, more aesthetically pleasing that my hack. Remember that I never believed it was the best code I’ve ever written, so if the code actually worked correctly I wouldn’t have cared. But it didn’t. It had fixed one small problem with my code but had introduced at least one new problem, one that was far more difficult to fix than the problem it was trying to solve.

There’s a technical, software engineering, side to this and there’s the effect is had on me. If I was being grand I suppose I’d call that the psychological side. I would like to talk about both of these aspects.

First, let’s discuss the technical side.

When modifying a large, established code base I have always believed that the correct approach is to make as few, targeted changes as possible to get the job done. The problem with a non-trivial code-base is that embedded inside it is dozens of small tweaks that you would never think of making but the software has accumulated in the School of Hard-Knocks. Real life has a tendency to throw up scenarios that, theoretically, are not possible. No matter how good you are at writing code these things happen.

This changed violated this principle. That alone annoyed me.

Of course the counter-argument is that we should be continually refactoring the code. This is the Extreme Programming approach and is one that I have [talked about previously](extremeprogramming.html). I do have some sympathy for this argument, except that in this case it t really apply. While the new code was undoubtedly cleverer than the code it replaced, it’s difficult to say that it’s better. When you’re writing code that may well be around in a number of years time it needs to be understandable. Writing clever code can be a disadvantage. A few extra lines of code, if they’re simple and easily understood, are often a good thing. It’s easy to forget that it’s not just the computer that needs to read the code.

Naturally the reason that people do this is that it’s much easier than reading and understanding the code, and this is probably more true in the language that we use than most (it’s a proprietary one that you won’t have heard of). So the author of the new code will have saved himself a few hours of work but by creating a clever yet difficult to understand alternative he has generated more work and confusion for legions of support analysts in the future. This costs the company time and money, although the author of the new code appears to be a super-hero as he checked in hundreds of lines of new code compared with my much smaller number.

The psychological aspects are less easy to define but in many ways are more important. Unfortunately I would concede that I am less capable of discussing them in anything like scientific manner. It’s not going to stop me trying, however!

The question at the centre of is all is: why do certain kinds of people like writing software? It’s a painstaking and fiddly task which requires unheard-of precision and attention to detail. Why would anyone want to do that?

I’m sure there are as many answers as there are programmers, but a common root cause would be the simple challenge of solving a complicated problem. There’s a certain satisfaction in completing something tricky and, even if you recognise that there are other ways of doing something, there’s usually a certain pride in the way you did it. It may not be the best, but it’s your way.

So really it’s one of those seven deadly sins: pride.

Also there is a large motivational aspect to it. At this point in the project I was already lacking my usual level of enthusiasm for a number of reasons that I won’t get into here. What kind of effect is someone unnecessarily rewriting my code going to have on me at this low ebb? Why would I want to write more code and make more fixes now? Surely it’s just going to get rewritten.

Note that I didn’t say “criticised.” I think an important aspect to get across here is that I am not above criticism. If the code had been improved, if the new author had discussed the options with me first and we’d agreed a way forward, I doubt that I would be writing this piece here and now.

Now there may well be some degree of bitterness here, however I think ll agree that there are both technical and human factors reasons why things should have been different.