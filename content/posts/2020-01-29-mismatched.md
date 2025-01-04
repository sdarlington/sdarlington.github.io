---
id: 64732
title: Mismatched
date: '2020-01-29T17:50:07+00:00'
author: 'Stephen Darlington'
excerpt: 'Sometimes you just need to walk in someone else’s shoes. But then you need to give them back.'
layout: post
guid: 'https://www.zx81.org.uk/?p=64732'
aliases: ['/computing/opinion/mismatched.html']
categories:
    - Opinion
tags:
    - Computing
    - enterprise
    - Opinion
    - startup
---

<span style="color: var(--color-text); font-size: 16px; font-weight: 400;">Here’s something I’ve seen a few times recently: a startup issues a patch for a critical issue seen by one of their large customers. The “enterprise,” however, takes a week to install and test it. Clearly, the startup concludes, if it takes a week to </span>*try*<span style="color: var(--color-text); font-size: 16px; font-weight: 400;"> a patch it can’t be </span>*that*<span style="color: var(--color-text); font-size: 16px; font-weight: 400;"> urgent or the staff are dumb, or, quite likely, both.</span>

Separately, we all know that a [big difference between a startup and an enterprise is process](https://seths.blog/2019/08/rules-and-responsibility/). So why do people suddenly get angry and start to lack empathy when that difference is exposed?

What we saw in the first paragraph is normal in big companies where you can’t just promote changes into UAT, much less production. It doesn’t matter how loudly you shout at their operations team, it’s not going to make any difference. Maybe the process requires writing test logs and rollback plans. Perhaps it has to be deployed and run in the pre-production environment first. It likely needs sign-off by the QA and security teams. With the best will in the world, this just can’t be done in a few hours, no matter how critical the issue is. Who is to say that the patch isn’t *worse* than the problem it’s trying to fix?

The difference is frustrating, but don’t mistake tedious process with a lack of urgency or incompetence. Circumventing process can take longer than following it and your client probably knows that. If nothing else, these people might lose their jobs by not following the right process!

Work with it, understand their constraints. This isn’t the time to lose that empathy. It would help if you also had humility and understanding. You know your product but *they* understand *their* systems, including how your software interfaces with the other applications they have running in their data centre.

And yes, working with their process is more complex and time-consuming. This is why we charge enterprises more for, ostensibly, the same features.