---
id: 73339
title: 'Why Enterprise Software is Bloated'
date: '2022-08-23T17:12:00+01:00'
author: 'Stephen Darlington'
excerpt: 'Enterprise software tends to be big and bloated and complex. Why is that? And what can we do to fix it?'
layout: post
guid: 'https://www.zx81.org.uk/?p=73339'
permalink: /computing/opinion/why-enterprise-software-is-bloated.html
categories:
    - Opinion
tags:
    - development
    - enterprise
    - Software
---

<span style="font-size: revert;">I confess that I’ve stolen the title of the post from </span>[elsewhere](https://www.mailbox.my/blog/posts/why-enterprise-software-is-bloated/)<span style="font-size: revert;">. My objective here is not to detract from that post, which is great, but to build on a few points that I </span>*thought*<span style="font-size: revert;"> it was going to make but didn’t. To make it clear where I’m coming from, here’s </span>[a Tweet](https://twitter.com/sdarlington/status/1489618760180944897?s=21)<span style="font-size: revert;"> that I wrote some time before I read that blog:</span>

> People who complain that “enterprise” software is too expensive have clearly never come across the bizarre, arbitrary and nonsensical policies and rules these companies have. It’s not unusual to have two customers with contradictory policies.

Alex’s post assumes that bloat is unnecessary and could be optimised away with better engineering. There are always counter-examples, but, in general, this is not my experience.

The key is to realise two facts:

1. Large companies have lots of rules and procedures
2. Large companies have a lot of leverage over software companies

My favourite rules and processes are always about [corporate security](https://twitter.com/sdarlington/status/1499369395558174725?s=21):

> The game of cat and mouse begins: I need to send a file to a client, but which method will actually make it through their corporate security? So far I’m down 2–0 but I’m not giving up yet.

Corporate security is focused very much on stopping Bad Things from happening. Undoubtedly that’s one part of the job. The part that usually gets forgotten is to allow people to do their jobs securely. Without these “safe routes,” the security is making everyone’s life harder and increasing costs but without improving security.

Here’s a lightly fictionalised example. A client has a production outage. We need to see their log files to diagnose the problem. Dropbox, Box and Google Drive are all blocked. They don’t have a corporate file share. It’s not possible to email them, because the logs are large and ZIP files are forbidden. We can’t screen share, since they blocked Zoom (our tool) and corporate policy means they can’t open a Team’s call with outside people. There is a special dispensation for this, but it’s only available for client-facing staff. And, in any case, needs to be applied for in advance. In the end, we went Old Skool, zipped the files and renamed them with a “TXT” file extension and that worked.

There’s a lot to unpack here. First: the security measures didn’t work. Despite the obstacles, we managed to transfer the files. It just took multiple well paid people a lot of time to figure out. There was no known supported tool available to facilitate this use case which, let’s not forget, was an outage of one of their production systems, something that customers pay them actual money to be able to access.

As ever, the individual rules make some sense, but together they make a *system* that doesn’t work for anyone. It annoys staff, adds delays to tasks and in many cases does not work anyway.

Let’s circle back to the original question: why is enterprise software bloated?

The short answer is that vendors need to be able to support enterprises *despite* all that unique processes. A task, like copying log files, that *should* take minutes might take hours. Ultimately that needs to be paid for.

Many of the processes and procedures are unique to an individual enterprise. This means that the vendor has no option but to write custom software to accommodate them. These changes get folded back into the product and every other customer gets a copy of them, but hidden behind a feature flag.

Multiply this by every customer and you end up with a vast number of options, the majority of which are not used by most customers. It’s a bit crazy. It’s bloated, hard to keep track of and hard for the vendor to test.

If everyone recognises the problem, what is the solution?

Some companies just lay down the law: this is the right way to do something; take it or leave it. You can do this for consumer software or if you have millions of customers. There’s only so much negotiation you can do with Microsoft for your Windows or Office licence.

Companies that do this for “enterprise” software tend not to be very successful. There’s a reason that Google Cloud is a distant third, well behind AWS and Azure.

You can make “consultingware,” that is, software with a core that it heavily modified for each customer. At a certain point you don’t even have a product any more, with disadvantages for both the vendor and the user.

Or you can make a single product with switches that enable or disable all these esoteric options. Either way, all your customers end up paying extra for the privilege.

In the end, as long as big companies continue to customise their environments in mutually incompatible ways, “enterprise software” is going to be expensive and bloated.