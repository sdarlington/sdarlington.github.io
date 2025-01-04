---
id: 70603
title: 'Adventures in iCloud Mail Hosting'
date: '2022-03-08T17:40:00+00:00'
author: 'Stephen Darlington'
excerpt: 'How does switching email hosts disable your Bluetooth headphones?'
layout: post
guid: 'https://www.zx81.org.uk/?p=70603'
aliases: ['/computing/opinion/adventures-in-icloud-mail-hosting.html']
spay_email:
    - ''
categories:
    - Opinion
tags:
    - apple
    - email
    - google
---

How does switching email hosts disable your Bluetooth headphones? Read on to find out.

As many people did recently, I got The Email from Google telling me that my [Apps for Domains (Legacy) account is going away](https://9to5google.com/2022/01/19/g-suite-legacy-free-edition/) and that I should either pay up or move away.

I’m not averse to paying. I use email a lot and I have my own domain, so I appreciate that I’m not a typical consumer. But I do object to paying Google because it feels like they’re double-dipping: both [data mining my information *and* billing me for the service](https://arstechnica.com/?p=1831215)<sup>[1](#fn1-24775 "see footnote")</sup>.

In short, I’m not going to stay with Google.

Since I already pay for iCloud — as part of the [Apple One](https://www.apple.com/apple-one/) bundle — moving my email there would be the obvious choice. Being able to use your own domain is a recent feature, part of [iCloud ](https://www.apple.com/icloud/) to use their current branding.

Unfortunately the documentation isn’t great. And there are technical gotchas. Let’s walk through my experience.

Step 1, enter your domain name. Okay, check.

Step 2, enter any existing email addresses. I entered my main address and it told me that it wasn’t allowed. As [others have noted](https://domlaut.com/icloud-custom-email-domains-should-be-better/), the system *does* return useful error messages, however those are not displayed on the screen! I was left guessing, which is incredibly frustrating.

I figured – partly luck, partly a process of elimination – that the email address was associated with another Apple ID. I logged into my other Apple IDs and removed references to my address, but to no avail. It continued to reject me.

The difficulty is that I’ve been using Apple’s web services for a *long* time. I have accounts that date back twenty years, before iCloud, before MobileMe, before your Apple ID even needed to be an email address. My main email address predates even that.

Luckily Apple has a “find your Apple ID” tool that tells you the Apple accounts that an email address is associated with. It turned up two accounts that I have no recollection of ever creating. One was a pre-email address account with a very bizarre name. It was an odd reference, but one I recognised so it was certainly me!

I requested that those two accounts get deleted. At that point, the “add domain” screen allowed me to continue.

My hope for step 3 What was to add some email aliases. The way I had my mail set up at Google was with a single mailbox but with multiple aliases. In practice, most of the aliases were just “wildcard” addresses, that is, if it found an address it didn’t know it would send it to the main mailbox. I knew that (bizarrely) Apple’s iCloud didn’t do that. I’m not totally happy with that but, for the way I use email, it’s not an absolute dealbreaker.

Except. You can’t have aliases. I *can* create an alias to my *iCloud* address, `somethingelse@icloud.com`, but *not* `somethingelse@mydomain.com`.

This is a problem. Over the years, I’ve removed almost all of the aliases, but one I use almost every day is the one attached to my Apple ID!

I go through my last few months of email – *that* was a fun afternoon – updated my address at a handful of companies so that the only remaining required alias was the one for my Apple ID.

I have payments and purchases and subscriptions for the entire family associated with this account. I know that *in theory* I can change the ID but in practice it fills me with dread.

If I’m to move my email, however, this is a necessary step. That it’s the one remaining required alias and that it might make things easier moving to *any* other email provider pushes me to attempt it.

It wasn’t as difficult or as problematic as I feared. All the work I did previously, removing all traces of the “old” Apple IDs, meant that the change largely Just Worked.

For the next day I found myself signing into all my devices again. The most surprising was when I started listening to a podcast and two minutes later my AirPods suddenly stopped working. I tried turning them off and on again – all the usual diagnostic tools – but couldn’t get them going. I was stood in the middle of the street so I didn’t want to get *too* in depth.

When I got home I realised they stopped working because they were connected to my Apple ID. I re-paired them with my phone and the audio immediately started to play. Of all the things I expected to stop working when I changed the account, my earbuds were not on the list!

As I write this, it has been about three weeks since I “flipped the switch” and moved over to iCloud email. My Google account is still live – I can switch back if something is utterly broken – but I have not done so. I guess it’s possible that I’ve missed some emails, but I would have no idea if I did, of course!

Despite the initial teething problems I’ve written about above, it’s been working well since then. It even supports *push* email rather than polling periodically. Not critical, but a nice feature.

Would I recommend it? With reservations. It’s not going to work as a replacement for Google for some people. And both the software and the documentation needs work. The feature set is limited, the backend supports more detailed diagnostics than the front-end and the documentation assumes that you don’t have a mess of Apple IDs like I do.

Let’s hope that Apple work on this. Sadly, I don’t think it’s going to be an overnight thing. There are a bunch of issues here, many of which appear to be a consequence of decisions made years ago.

<div class="footnotes">---

1. The argument may well go that they do not data mine paid accounts but I have no ability to verify that. Google have done enough dodgy things with data that I don’t trust them. Pick one. [↩︎](#fnr1-24775 "return to article")

</div>