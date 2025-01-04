---
id: 3617
title: 'Familiarity Breeds Contempt'
date: '2013-03-14T20:24:35+00:00'
author: 'Stephen Darlington'
excerpt: 'Earlier this week I presented at the London iOS Developer Group meeting. Here''s what I talked about.'
layout: post
guid: 'http://www.zx81.org.uk/?p=3617'
aliases: ['/computing/opinion/familiarity-breeds-contempt.html']
categories:
    - Opinion
tags:
    - api
    - development
    - ios
    - presentation
---

This week I did a presentation at the [London iPhone Developer Group meeting](http://lanyrd.com/2013/lidg49/). Given my experience with using lots of APIs, I thought it might be a good, if dry, topic. I tried to spice it up by complaining about lots of them and trying to condense that negativity into some useful lessons to take away.

Most of the other discussions of this subject that I’ve seen focus on [designing](http://mattgemmell.com/2012/05/24/api-design/ "http://mattgemmell.com/2012/05/24/api-design/") [libraries](http://ignorethecode.net/blog/2013/02/28/api_design/ "http://ignorethecode.net/blog/2013/02/28/api_design/") but I thought the same lessons could be applied to all kinds of interfaces, from Objective C libraries to REST API’s for connecting to web services. (I don’t mean to suggest that the focus of the two articles I link to is wrong. They’re both very much worth reading.)

You can see a [PDF of the slides here](https://www.dropbox.com/s/x780wkl4zaycbnh/API.pdf) (though they might not make much sense without what I was saying at the time), but the gist is as follows:

- Design your APIs around use-cases. Many appear to be designed around “how can I made the data I have available.” This is the wrong way round
- Clients need to access data in a predictable, reliable way. Being clever <s></s> accepting any old junk and trying to do the right thing <s></s> is often not the right thing to do
- Communicate how it works and how it’s going to change clearly. Examples and sample code are always useful
- Think about error cases. “[Something went wrong](https://delicious.com/developers/addnewbookmark "https://delicious.com/developers/addnewbookmark")” is not a good error message
- Think about the devices that people are likely to be accessing your service from. Mobile apps have latency, bandwidth and CPU constraints that desktop computers and other servers do not. The iPad 4 has more resources to throw at a problem than an iPhone 3GS. Your code might need to work on both
- Be consistent. Make your API look like other, similar APIs and use the patterns of the technology you’re using. That means delegates and return codes for Objective C, inheritance and exceptions for C#
- And, most importantly, use your own API. Don’t keep special “secret sauce” for your self. How else are you going to know whether it works than by actually using it?

Ideally I’d end a presentation (or blog post) with salient advice on the best way to do something. This is an exception. I don’t think there’s a one-size-fits-all solution and I’m generally weary of Best Practice guides.

So I’ll end by noting that poor APIs result in poor applications. It’s worth investing the time and energy in doing it well. Your users <s></s> and your future self <s></s> will thank you.