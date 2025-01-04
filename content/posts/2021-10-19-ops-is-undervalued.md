---
id: 69947
title: 'Ops is undervalued'
date: '2021-10-19T17:39:00+01:00'
author: 'Stephen Darlington'
excerpt: 'Despite being the people that keep your software up and running, ops teams often don’t get the credit they deserve. Why?'
layout: post
guid: 'https://www.zx81.org.uk/?p=69947'
aliases: ['/computing/opinion/ops-is-undervalued.html']
spay_email:
    - ''
categories:
    - Opinion
tags:
    - business
    - computer
    - engineering
    - management
    - Software
---

<span style="font-size: revert; font-weight: 400;">I made the mistake of suggesting that there was a blog to be made from </span>[this tweet](https://twitter.com/endocrimes/status/1353735484862836745?s=21)<span style="font-size: revert; font-weight: 400;">. This is that post.</span>

> People still underestimate the value in (Developer|Operator) Experience when building platforms and honestly it’s kinda shocking to me.
> 
> If you want to win mindshare you need to make your tools actually usable. If you don’t want to lose it you need the same.

First: I agree with the sentiment. Maybe not to the same extent as Danielle, but I fight the same battles in my day job. I wanted to say this now because, on reading the rest, you may think the opposite. What follows is an *explanation* of why this is a common situation. I don’t mean it as a *justification*.

In summary, making software work for ops teams is not a focus either for software companies or internal development teams because of at least three reasons:

- It’s not a business driver
- Ops are not the buyer
- Engineering is run by developers

Naturally there are exceptions to these rules. Every company is different. These are observations, not rules.

Working at the “coal face” it’s easy to forget, but people don’t buy software. They buy a *solution to a business problem*<sup>[1](#fn1-27903 "see footnote")</sup>. These days, that solution is often software but you don’t buy a new product because it’s cool<sup>[2](#fn2-27903 "see footnote")</sup>.

A driver might be to get a report generated more quickly, or to provide a new service to paying customers, or to reduce the costs of some infrastructure<sup>[3](#fn3-27903 "see footnote")</sup>.

But, you argue, the ops team are the people who keep the system up and running. How can this new system generate reports or deliver a service if it’s not running reliably or has not been provisioned correctly?

You’d be right. Sadly, organisations are often not structured to recognise that fact. The IT teams tasked with making everything run smoothly are frequently in a completely different reporting hierarchy from “the business.” I put “the business” in quotes as I hear it described that way *all the time*, but it’s this us-versus-them philosophy that brings many issues, including how ops get sidelined<sup>[4](#fn4-27903 "see footnote")</sup>.

With “the business” and “ops” being in separate reporting structures, one or the other has to sign off on the purchase of new software (unless it goes *way* up the organisation) and that’s always going to be “the business.”

The buyers normally *consult* the ops team, but ultimately they’re going to put their own needs first. Objections that the ops team have will end up *in* the business case, but likely in an appendix that no one will ever read.

This makes no sense because, as we all know, most of the expense of a system occurs *after* go-live. But monitoring, management and deployment are not things at the top of mind of developers and business users.

But even in the IT organisation, the ops team frequently don’t get the attention they deserve either. Anecdotally, this is because IT leadership come from the development team. Their outlook on IT is therefore skewed towards *making things* rather than *keeping them running*. I see the same challenges for testing teams. Or, indeed, the lack of testing teams.

This lack of buy-in from the ops team is endemic. I see it in companies buying and using software. I see it in companies that make and sell software<sup>[5](#fn5-27903 "see footnote")</sup>.

At this point, what I would like to be able to do is say, “And the solution to this terrible problem is…” Sadly there is no easy answer. Saying “You should listen to your ops team” is both obvious and unhelpful. Making tools *useful* for the ops team to get mindshare is a good way to get your software on a shortlist but maybe not enough to clinch that sale.

<div class="footnotes">---

1. I’m talking here about software used in a business of course, but the difference between this and personal use isn’t as great as you might initially imagine. You buy a game to solve the “problem” of boredom. Very few people buy software *because* it’s software. [↩︎](#fnr1-27903 "return to article")
2. You might buy it because this, specific solution is cooler than the other options. [↩︎](#fnr2-27903 "return to article")
3. That is, even in the case where it’s the infrastructure that is being improved, the business case is not “make the ops team more efficient” but “make the cost of operations lower.” [↩︎](#fnr3-27903 "return to article")
4. There’s another blog in how toxic “the business” as a concept is. This isn’t that blog. [↩︎](#fnr4-27903 "return to article")
5. This is a chicken and egg problem. Do software companies fall into this trap because they’re run by developers? Or is it because they’re selling to companies who have already fallen into the trap? [↩︎](#fnr5-27903 "return to article")

</div>