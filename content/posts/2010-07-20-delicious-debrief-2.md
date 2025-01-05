---
id: 2151
title: 'Delicious Debrief (Part 2/5)'
date: '2010-07-20T20:42:14+01:00'
author: 'Stephen Darlington'
excerpt: 'Developing iPhone software isn''t all sex, drugs and rock and roll. Sometime you have to make difficult changes because of things outside your control. Here is part two of my story from late last year.'
layout: post
guid: 'http://www.zx81.org.uk/?p=2151'
aliases: ['/computing/opinion/delicious-debrief-2.html']
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

Last year Yahoo! announced, with no notice, a significant change that had far reaching consequences for all third party applications including my iPhone program, Yummy. This is the second in a series of posts that discusses how I dealt with it.

[Yesterday](http://www.zx81.org.uk/computing/opinion/delicious-debrief-part-15.html) I spoke at a high level about my iPhone application and some changes that Yahoo! made to their side of the system. Today I’d like to talk in a little more detail about how those changes were announced and why they were tricky.

### The announcement

On 19 October 2009, [Yahoo! posted a blog announcing that all new accounts would be accessed with a Yahoo! ID](http://blog.delicious.com/blog/2009/10/delicious-is-now-about-you-too.html).

As far as I know, this is the first time that anyone outside Yahoo! knew about this change. And the change took effect immediately.

At the time of the announcement, Apple were taking around two weeks to approve updates to iPhone applications. This means that even if it took no time at all to make the required changes — which as we’ll see is far from the case — it would still mean that a user of Delicious.com would have approximately two weeks to wait before *any* third party application would support their new scheme.

I don’t necessarily expect Yahoo! to support me personally but I *do* expect them to act in ways that are beneficial to their own users. Knowing that no third party applications would work with new accounts clearly does not meet this goal.

Maintaining a healthy ecosystem around their own software with well maintained, documented and supported APIs seems to work to their advantage, yet they did not do this. Just look at the flourishing market for Twitter clients for an example of it done well.

But, put bluntly, they failed.

It took over a month to update the API documentation. And when they did they simply added a one paragraph note saying that authentication can now be performed using OAuth. Until that point the only official resources were a few responses in the Delicious discussion forums.

Now, months after the change went live, the documentation is still barely adequate to code against. I think the lack of other third party clients that support Yahoo! ID authentication reinforces this point. (At the time of writing, I think I’m right in saying that Yummy and Yummy Browser are the only two iPhone clients that support Yahoo! ID logins.)

Unfortunately the haphazard approach to developers was only the first part of the problem.

### Surely it’s just a different username and password?

You’d think that using a Yahoo! password rather than a dedicated Delicious password would be pretty easy, but you’d be wrong.

[OAuth](http://oauth.net/), as it’s called, doesn’t work like that.

The idea is that you shouldn’t have to trust anyone other than Yahoo! with your Yahoo! password. So, bizarrely, I had to make Yummy work without ever knowing what your username or password is!

Without getting too bogged down in detail, this is roughly how it works:

1. The client launches a web browser. Since an iPhone can’t multi-task third-party applications, this means exiting and switching over to Safari[^1]. The changes announced for iPhone OS 4.0 don’t help here
2. The user logs into Yahoo! The server responds with a code
3. The user launches the client again and enters the code

Then every time the client wants to access a protected resource it does some cryptographic magic using the code (generating what’s called a “hash”) and sends that along with the request.

But the devil, as ever, is in the detail. The detail in this case is a twelve page document that assumes that you know what things like “octet string, first base64-encoded” means. Therefore in practice you end up looking up every second paragraph which slows things down.

Of course, writing the code yourself would be the hard option. For a standard such as OAuth there are bound to be some Open Source libraries that can be used without too much trouble.

### Next…

Tomorrow [I’ll talk about those Open Source libraries](http://www.zx81.org.uk/computing/opinion/delicious-debrief-3.html) and what I ended up using.
[^1]: The iPhone OS does allow applications to include an embedded web browser, indeed Yummy already has one to allow users to preview their bookmarks. However, the OAuth specification recommends against this approach for authentication. The idea is that you should only trust Yahoo! with your username and password and that entering them into a third-party application might break that trust. An early version of the change did include an embedded browser and I may yet revert back to that version.
