---
id: 3112
title: 'iOS Developer Program: from individual to company'
date: '2011-08-30T18:51:28+01:00'
author: 'Stephen Darlington'
excerpt: 'Despite what you may have heard, it is possible to move an iOS Developer Account from an individual to a company. Though it''s not necessarily all plain sailing. Here is my experience.'
layout: post
guid: 'http://www.zx81.org.uk/?p=3112'
permalink: /computing/opinion/ios-developer-program-from-individual-to-company.html
image:
    - ''
embed:
    - 'This is the default text'
seo_follow:
    - 'false'
seo_noindex:
    - 'false'
categories:
    - Opinion
tags:
    - app
    - apple
    - appstore
    - development
---

I thought it was worth writing about my experience converting my iOS Developer Program account from an individual to a company since a lot of people [on Twitter](http://twitter.com/sdarlington) were taking an interest. I can’t claim objectivity or that my experience will mirror yours, but hopefully you can be better prepared than I was.

First things first. Can you even make the transfer? Despite claims to the contrary, it *is* possible. I think the process is often confused with the ability to move applications or whole accounts between companies (which isn’t currently possible).

It’s all covered in the FAQ which [reads like this](http://developer.apple.com/support/ios/enrollment.html):

> **If I enroll as an Individual, can I change to a Company later?**
> 
> To convert your iOS Developer Program Membership from an Individual to a Company please contact us. As part of the conversion process, you may be asked to submit business documents proving your company&#146;s identity.

As the link in the FAQ requested, I send an email using the “Contact us” form. Just over two business days later they replied saying that I needed to give them a call. It’s not clear why they couldn’t have just said that in the FAQ!

The next morning I rang. They answered immediately but it was a poor line, though this could have been Skype. Despite that the call only took a couple of minutes.

He explained that the provisioning portal would not be available while the process was being completed and that I would not be able to upload new binaries, either updating existing applications or creating new ones. This could take anywhere from a few days to a few weeks.

Sure, fine, that’s what I was expecting. He said I would get an email in a few minutes; I should follow the instructions on that.

Knowing that I wouldn’t have access to the provisioning profile, I updated my certificates and was pretty confident that I wouldn’t need to make a new release for a few weeks.

The email came pretty much immediately. There’s some web form to fill in. Now I’m back full-circle. Why did I need to call if I need to go to a web page to start the process?!

The form requests the kind of information you’d expect: company name, address, names/addresses of the people with legal authority over the company. I was expecting to have to give the company number, but the didn’t ask for that at this stage. And I wasn’t expecting the company website URL to be a mandatory field, but it was. (I created a temporary Google Sites page for the purpose.)

Clicking submit, Apple now say that they will review the application.

They did not, however, tell me that I would effectively no longer be a paid member of the Developer Program. This meant that I could not access the iOS5 betas that had just started circulating. I had already installed beta two on my iPad and a matching version of the SDK on my MacBook, so it wasn’t too bad initially. I would revise this opinion later on.

A couple of days later, Apple requested information about my company. *By fax*. Here’s a company that thinks that DVD-writers are last years technology and it’s insisting that I use a fax machine to communicate with them!

[![Dilbert.com](https://i0.wp.com/dilbert.com/dyn/str_strip/000000000/00000000/0000000/000000/70000/5000/900/75991/75991.strip.gif)](http://dilbert.com/strips/comic/2009-12-10/ "Dilbert.com")

I replied to their email, including their reference number, attaching an electronic copy of the documentation that they had requested. I offered to send a fax if that was not acceptable.

A couple of days later I received an acknowledgement from Apple, so I assumed that all was okay.

Weeks passed.

(Okay, that might be a little melodramatic.)

No access to iTunes Connect was a little inconvenient but things got worse at the beginning of August when iOS 5b2 expired meaning that my iPad was unusable.

I pinged an email to Apple asking about the progress of my application but received no reply.

I think that I was remarkably patient under the circumstances. I waited another three weeks before I sent another message. And then, poking around the parts of the Developer Support website that I could still access, I found that there was a ‘Contact us’ form with a specific ‘Let me know about the progress of my enrolment’ option, so I sent a message from there as well.

That was on a Friday evening. I’m still not sure what hours they work — whether the have local teams or only operate on US hours — so I wasn’t expecting anything to happen immediately.

On Monday, just before nine in the morning as I was heading into my day-job, I got a call from an unknown US number. It turned out to be Apple.

The good news was that my transfer had been approved. I would need to accept the Developer agreement again — last time it was for me as an individual, this time for me as a director of my company — and then I would be all set. There was no acknowledgement or apology of the amount of time it had taken and I didn’t feel like pushing the point. I assume that one of my messages prompted the call and the approval, but whether my virtual prod was actually required or not is anyones guess.

I accepted the developer agreement and immediately got *some* of my access rights back. I could access the Member Centre for example but it took until later the following day before the App Store showed my company name. Shortly after *that* I got full access to iTunes Connect again.

So, in short, the process is both possible and works. If I had to offer any advice, I would suggest assuming that the process could take a couple of months and that during that time you would have *no* access to anything currently covered by an NDA, including beta releases and iTunes Connect. If it goes quicker for you, great. If not, at least you’ll be better prepared than I was.