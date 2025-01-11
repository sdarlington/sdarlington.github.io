---
id: 460
title: 'Why "unlimited" broadband must die'
date: '2008-04-15T06:00:19+01:00'
author: 'Stephen Darlington'
layout: post
guid: 'http://www.zx81.org.uk/?p=460'
aliases: ['/computing/opinion/why-unlimited-broadband-must-die.html']
categories:
    - Opinion
tags:
    - Computing
    - Opinion
---

In a [previous post about Internet Service Providers](/computing/opinion/net-neutrality-privacy-and-hypocrisy.html) I hinted that their current business model — where it’s possible to download as much as you like when you like — was unsustainable. Since I’ve had a few people asking me about that I thought I’d dig into the subject.

The first question that we need to ask before we get any further is, What does your ISP do? This may look like a silly question at first glance but exactly what data they pass where is the key to understanding how they make (and lose) money.

Unfortunately the answer gets rather complicated very quickly so I’m going to make some assumptions. First I’m going to assume that you’re in the UK. Second, that you’re using ADSL and not cable or something more exotic. And thirdly I’ll assume that your ISP hasn’t “unbundled the local loop.” If you don’t know what this means[^1] you can be reasonably sure that the following is, if not correct, then fairly close to the truth.

Let’s look at what happened when you tried to download this web page.

1. The request went from your computer to your router or modem.
2. Your phone line is owned by BT, so they (and not your ISP) pick up the request.
3. BT move your request around the country trying to find the nearest connection to your ISP.
4. BT hands over the request to your ISP.
5. Your ISP does not have direct access to every site on the Internet. Instead they probably pass your request onto another supplier. This is called “peering.”
6. This other supplier actually ends up talking to the machine that this web site is hosted on.

The interesting thing about this is that the bit that your ISP directly controls is actually fairly small. Of course there’s much more to it than I have listed above and it’s clearly an important part, but fairly small nevertheless.

Your ISP pays both BT and the peer for their services. BT get paid both for the number of customers and for the amount of data flowing the over the network. And the peers also charge by the amount of data transferred.

Yet you most likely pay a fixed fee for your Internet connection.

There is nothing intrinsically wrong with a supplier receiving a fixed payment and paying a variable fee. This happens all the time. For example your mortgage may well be fixed rate even though the rate that your bank pays to borrow the same money is highly variable. And the wholesale price for gas and electricity varies on an hour-by-hour basis yet your tariff only changes once or twice a year.

However, two things have been happening in the consumer Internet connection world.

Firstly usage has been rocketing upwards. An increasing number of people are using high-bandwidth sites such as YouTube and the BBC iPlayer, and services such as movies downloads and iTunes[^2].

On the other side prices have been pushed down, with companies offering free broadband when taken with another service and other ISPs having to respond.

The cost of bandwidth does, of course, drop over time and ISPs are also consolidating which also reduces their overhead, yet I think it’s fair to say that usage is increasing faster than costs are dropping.

Okay, so that’s the problem. What is the solution?

An unrealistic solution, and one I see fairly frequently from the people that tend to download the most, is that the ISPs should just bite the bullet and provide the service that they promised. They said “unlimited” so they should *mean* unlimited. I have a certain sympathy for this argument, in the sense that it’s a problem that the ISPs have made for themselves. However it should be clear that the numbers just do not add up.

The ISPs are choosing a second option: either selling their users surfing habits to third-parties or billing popular websites for access to their customers. Both seem to be abusing their own customers, and yet there is still no guarantee that these new revenue streams will cover the increasing costs.

It seems to me that the only solution that would work on a large scale is to charge end-users for the bandwidth that they actually use[^3]. This may not be popular in the short-term, but it’s a whole lot better than them limiting what services you can use and when.
[^1]: If you do know what it means any want the hard numbers, have a look [on the plus.net blog](http://community.plus.net/blog/2008/02/28/how-uk-isps-are-charged-for-broadband-the-cost-of-ipstream/).
[^2]: Some people pin the blame on illegal downloads over peer-to-peer services. I deliberately left that off the list as typical bandwidth usage is drastically increasing even if you exclude infringing activities.
[^3]: Of course the most likely scenario would be “bundles” of bandwidth, much as you buy bundles of texts or minutes for your mobile phone.
