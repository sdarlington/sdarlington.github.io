---
id: 2152
title: 'Delicious Debrief (Part 3/5)'
date: '2010-07-21T20:20:57+01:00'
author: 'Stephen Darlington'
excerpt: 'Developing iPhone software isn''t all sex, drugs and rock and roll. Sometime you have to make difficult changes because of things outside your control. Here is part three of my story from late last year.'
layout: post
guid: 'http://www.zx81.org.uk/?p=2152'
aliases: ['/computing/opinion/delicious-debrief-3.html']
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

### The story so far

Last year Yahoo! announced, with no notice, a significant change that had far reaching consequences for all third party applications including my iPhone program, Yummy. This is the third in a series of posts that discusses how I dealt with it.

[On Monday](/computing/opinion/delicious-debrief.html) I gave an overview of the problem and [yesterday](/computing/opinion/delicious-debrief-2.html) I looked at how those changes were announced and why they were tricky. Today we’ll look at how I actually implemented those technical details — though not at the code level so don’t worry if you’re not a programmer!

### Open Source OAuth

The two leading contenders are [OAuthConsumer](http://code.google.com/p/oauthconsumer/) and [MPOAuth](http://code.google.com/p/mpoauthconnection/). It’s only fair to note that my evaluation of both projects was in October and November 2009. Progress is likely to have been made on both projects since then.

I managed to get the sample projects for both up and running pretty quickly. However on trying to log in I immediately came across a problem. Yahoo! displayed a big warning message suggesting that you don’t authorise any new applications for security reasons. And, worse, that this method of authenticating was going to be removed in a few months.

Even if I could get it working this was going to be a show-stopper. I couldn’t in clear conscience ask users to ignore such a prominent message. It took a long time pouring over the code and the OAuth specification to realise that what changed was the OAuth specification itself.

As the error message noted, due to a security flaw in OAuth 1.0 they issued an update to the specification (called 1.0a) and it was *this* that Yahoo’s servers was objecting to. Neither library had been updated to the new version.

The change to both projects was small and straight-forward but I was worried that I actually needed to make any alterations at all. Were they being maintained? Was anyone using them?

It fairly quickly became clear that both projects were really optmised for connecting to, or at least developed against, Twitter. As with all standards, each implementation has their own peculiarities and specialisations. To be clear, there is nothing wrong with this. All code has its own axioms and its intended use defines its “shape.”

When I first looked at it, one of the things I liked about MPOAuth was that it did a lot of the hard work for you. It kept an internal state machine so that it knew which message it should be sending to the authentication server and what it should expect to see in return. I’m all for other people doing the work for me. As long as you followed the “correct” order everything worked just fine.

However, in a real world application you can’t expect users to do the right thing every time; there needs to be some way to recover from errors or allow people to change their minds. And, try as I might, I couldn’t quite figure out how to force MPOAuth to do what I needed. In trying to be clever it appeared to be making my life harder rather than easier.

OAuthConsumer got closer to being an integral part of Yummy. The way it’s structured was much more closely aligned with how I would have done it but I came across endless errors trying to connect to Yahoo’s servers. Most came back with very obscure errors and I spent a huge amount of time single-stepping (debugging) the framework — something that I’d hoped I could avoid by taking pre-existing code.

To be fair, much of this comes down to OAuth itself. On the server side there is no way to determine which parameter is incorrect, only that the request is not internally consistent.

### OAuth in Yummy

Having spent a lot of time trying to understand why the existing libraries did not work with Yahoo! I had accumulated a good understanding of the OAuth 1.0a specification but a much less clear understanding of the frameworks themselves. There was something about the way that they had both been put together that didn’t quite mesh with either my way of thinking or the way that I was trying to implement it in Yummy — I’m still not quite sure which.

So I decided to go ahead and make my own OAuth library. In some respects this was quite a risky move as it was going to be difficult code to write and it would be in a very fundamental part of the software, traditionally somewhere that I try to use simple, well tested code.

It’s difficult to say whether this was the quickest option. Maybe I could have changed one line in, say, OAuthConsumer and got everything working in half the time. But the amount of time that I spent struggling with them suggests not and this way I have full control over and full understanding of every line of code[^1].

I ended up writing about four hundred lines of new code instead of using MPOAuth or OAuthConsumer. This is some reasonably low-level code and was tricky to debug as the server-side typically responded with a simple “invalid signature” error no matter what the actual problem was. (This is not to complain about Yahoo’s service. It’s just the nature of the beast, unfortunately.) However, once written it’s proven to be surprisingly resilient[^2].

### Coming tomorrow

Having decided on the low-level technical details I discovered that there was [still a lot of work to do](/computing/opinion/delicious-debrief-4.html). That’s what I’ll be talking about tomorrow.
[^1]: I’m also geeky enough to *like* writing this kind of code. So shoot me.
[^2]: I’m only aware of one bug caused by the new code, and that problem, strictly speaking, was already present in Yummy, it just did not exhibit the same behaviour previously.
