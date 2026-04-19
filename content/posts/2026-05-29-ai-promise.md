---
date: '2026-05-29T10:27:40+01:00'
draft: true
title: 'AI: Promise'
author: 'Stephen Darlington'
layout: post
categories:
    - Opinion
tags:
    - intelligence
    - ai
    - technology
    - history
    - computer
---
Last week, we talked about [the history of AI](/content/posts/2026-05-22-ai-history.md). Today, I’ll share my experience. I don’t pretend to be an expert. I’ve not checked out every last facet of any particular AI.

If there’s one takeaway from this piece, it’s that AI can be used for real, useful things today. We’ll talk about the costs and sustainability next week, and, of course, your mileage may vary. Undoubtedly, they’ll get better, but even if we’re at a plateau then the technology is interesting and a timesaver for some applications.

Beyond random goofing around, the first time I did something _real_ with AI was when I got stuck making a change to my Wordpress plugin. I needed to do something _slightly_ out of the ordinary, meaning that the readily documented API didn’t work and the alternative looks like hand-coding the whole thing -- a lot of work. ChatGPT came up with a different API that did about 80% of the work. It _was_ documented but would have been difficult to find any other way[^wordpressapi].

I’ve made a little use of writing AI tools. Checking my grammar. Brainstorming ideas. Summarising long message threads. Most people seem to I know that it’s good for these things.

Recently I got to use LLM code gen in anger.

I started by trying to improve some GitHub Actions. I don’t play with Actions very often, so I normally end up doing lots of internet searches and experimenting. What I was looking to do would probably have taken an hour or two. I asked Claude to refactor my action and... in less than a minute it did. It worked first time.

But there were some warnings. I immediately started searching for a solution. It took me a minute of failed searches to realise that I had another option. I asked Claude again. Surprisingly, it found the task harder than the original refactoring exercise but it quickly and accurately found the solution again.

People who have been using AI for a while will probably be underwhelmed by this. _But it can do so much more!_ Yes, but I need to see it working and understand what it can be used for myself. This is my learning process.

Emboldened, I moved on to something more ambitious. It may be a perfect use case for AI. I was trying to interface between two systems, which means it was constrained and well defined. But it generated hundreds of lines of (seemingly) working code with little input. All while I was doing something else.

Could I have done it myself? Yes. Would my version have been better? Maybe, maybe not. But it's like my Roomba. I can do a better job of cleaning... but I have to actually do it. And I don't (honestly). I _could_ have written this code, but would I ever have found the time? Probably not.

The other question people will have is: is the code good? Are there any bugs? I’ll be honest. I don’t know. In my testing it works well. However, underlying that question is the assumption that _my_ code would have been bug free. Very likely it would not have been. My code would likely have had more comments, but I could have asked Claude to do that and it probably would have.

Like the robot vacuum cleaner or dishwasher, it's another "perfect is the enemy of good" kind of thing. It wrote _decent_ code. But, more importantly, I didn’t have to do it! I was able to do higher value work while it churned away in the background.

For a less well defined task, I would probably have had to provide more instructions, thinking about the task in more detail. But that would have been the case if I was to do the work myself or hand it over to someone else. We’ll get on to the risks next week, but I saw it more as an accelerator than threat to my job.

[^wordpressapi]: I’m not documenting exactly what I did in case ChatGPT failed to point out some massive security hole.
