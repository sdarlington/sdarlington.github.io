---
id: 1412
title: Communication
date: '2010-07-13T20:23:03+01:00'
author: 'Stephen Darlington'
excerpt: 'Communicating in the same language as your users is never as easy as you first think.'
layout: post
guid: 'http://www.zx81.org.uk/?p=1412'
aliases: ['/computing/opinion/communication.html']
adman_disable:
    - 'on'
categories:
    - Opinion
tags:
    - computer ßscience
    - Computing
    - engineering
    - Opinion
    - Software
---

“Do you ever change this type of trade?”

I was sat on the trading floor discussing a new feature that I was implementing with the person who would be using it the most.

“No, never.”

This was one detail of the change that would have far-reaching consequences in the code. A “no” would mean a few days of development, a “yes” would indicate several *weeks*.

“Are you absolutely sure? You don’t change it even once a month?”

I knew they’d like the smaller estimate but, equally, I knew that I didn’t want to end up trying to implement several weeks worth of functionality in the smaller time frame. I’ve seen that kind of thing happen too often.

“John[^1], we don’t ever change these trades do we?”

John was the head trader. If anyone would know it would be him.

He rubs his head and leans back, thinking.

“Why would you want to? No, I can’t see us ever changing one.”

Of course, you can guess what happened thirty minutes into the first trading day with the new software.

So, what happened here? Why did we get the requirements so wrong? And why did we only find the mismatch *after* the system was moved into production?

Both the problem and the solution is the same thing: communication. Or more precisely, communicating using the right language.

Some developers are happy to only “speak” technical, proud that they are masters of their programming environment but ignorant of their users problems or how they really use the software.

Above I started out correctly, I was trying to understand the traders business and talking in terms of booking trades, positions, legal entities and a bunch of acronyms that would make even less sense out of context.

But I made one error: I used the word “change” without defining what I meant. I meant, well, any change. And so did they. Yet they didn’t consider *moving* a trade from one book to another to be a change and, unfortunately, I did.

You’d like to think that there were checks and balances in place to make sure that this kind of thing didn’t happen. And there were. In addition to informal and formal testing, there was over a week of “parallel running,” where the traders had to use the old and the new system together and check that the results were the same in both of them.

Were there any *moved* trades during this time? Of course. Why did the traders not notice? Well, it was *about* right; the differences, while present, were explicable and so not considered significant enough to mention even though I asked to hear about any problems at all.

So, again, communication. Or at least human nature. I wanted to hear about *any* differences but they tried to help me by only talking about differences that they couldn’t account for.

What’s the answer? Well, I’m not sure there’s an easy one. “Understanding your user” is a short, simple phrase but hides so much. If you spent the time to fully understood their job you probably wouldn’t have the time to do your own. But finding the balance is crucial.
[^1]: Names have been changed to protect the… well, they work for a bank so I hesitate to say “innocent” but you know what I mean.
