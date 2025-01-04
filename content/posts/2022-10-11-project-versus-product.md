---
id: 76575
title: 'Project versus Product'
date: '2022-10-11T17:21:00+01:00'
author: 'Stephen Darlington'
excerpt: 'How can we set the expectation that companies should contribute to open source software projects?'
layout: post
guid: 'https://www.zx81.org.uk/?p=76575'
permalink: /computing/opinion/project-versus-product.html
categories:
    - Opinion
tags:
    - business
    - Computing
    - development
    - enterprise
    - java
    - opensource
    - Opinion
---

<span style="font-size: revert;">With the fuss about the </span>[Log4Shell vulnerability](https://en.wikipedia.org/wiki/Log4Shell)<span style="font-size: revert;"> finally dying down, it’s time to step back and take a good, long think about what happened and, more importantly, what can be done to stop it from happening again.</span>

[Sadly the prognosis is not good](https://apple.news/A5ISa5YRyShibjNdu_eXD4w). The tl;dr is both simple and obvious: we simultaneously like free stuff and getting paid for our own work.

Most companies treat open source software exactly the same as commercial software but with a much lower purchase cost. When the software goes wrong, we want *someone else* to fix it for us. Unfortunately, sometimes we don’t even know where the software comes from. In the case of [log4j](https://logging.apache.org/log4j/2.x/), it’s run by volunteers. There is no 24/7 help desk with eager employees waiting to take your call.

But even if there is a company that backs the project, one that does have engineering, QA and support staff, is it reasonable to expect an immediate fix to a vulnerability?

Whether a company backs it or not, using open source software is more like being part of a community than being a customer. I came across this phrase about free software a few years ago: “[If it breaks, then you get to keep both pieces.](https://english.stackexchange.com/a/250982)” It’s very apt here.

My small part in trying to fix this perception is by calling free software *projects* and commercially supported versions *products* or *services*.

The idea here is that the word “project” implies some degree of a work in progress, one that requires effort from all stakeholders.

In my Day Job<sup>[1](#fn1-22158 "see footnote")</sup>, I often see companies expecting to get commercial quality support for free because the software is free. By “commercial quality” I don’t mean “good.” The level of knowledge and support provided by most free projects is phenomenal. Instead, I mean that there are service-level agreements and *guarantees* of service within a particular time frame.

As it says in “[Cloud Without Compromise](https://www.zx81.org.uk/blog/cloud-without-compromise.html)”:

> But there is something to the old adage that “You get what you pay for.” (… there’s a world of difference between building systems for pet projects versus designing for the needs of enterprise.)

Those service level agreements [come with a cost](https://www.technologyreview.com/2021/12/17/1042692/log4j-internet-open-source-hacking/). If you want a fix or an enhancement, you’re welcome to *ask* a project for it, but it might never come or, if it does, maybe not on a timescale that helps you. The rules change when you pay for the help.

My hope is that those companies that only ever take from open source projects and never contribute learned a lesson. By helping keep the project healthy, you don’t even need to be altruistic. Think of it as insurance.

If you use the software, there are many ways you can “pay it forward”: share enhancements and fixes, write documentation, share your knowledge and experience to bring in more users, or help other users with community support. But if there’s a mechanism to pay for it, the simplest way for most users is cold, hard cash.

<div class="footnotes">---

1. An open source database, so I have both skin in the game and bias. However, I think I’d be saying the same thing even if I worked for a vendor of closed source software. [↩︎](#fnr1-22158 "return to article")

</div>