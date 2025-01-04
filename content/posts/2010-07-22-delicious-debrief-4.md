---
id: 2154
title: 'Delicious Debrief (Part 4/5)'
date: '2010-07-22T20:23:22+01:00'
author: 'Stephen Darlington'
excerpt: 'Developing iPhone software isn''t all sex, drugs and rock and roll. Sometime you have to make difficult changes because of things outside your control. Here is part four of my story from late last year.'
layout: post
guid: 'http://www.zx81.org.uk/?p=2154'
permalink: /computing/opinion/delicious-debrief-4.html
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

Last year Yahoo! announced, with no notice, a significant change that had far reaching consequences for all third party applications including my iPhone program, Yummy. This is the third in a series of posts that discusses how I dealt with it.

[On Monday](http://www.zx81.org.uk/computing/opinion/delicious-debrief.html) I gave an overview of the problem, [Tuesday](http://www.zx81.org.uk/computing/opinion/delicious-debrief-2.html) I looked at how those changes were announced and why they were tricky, and [yesterday](http://www.zx81.org.uk/computing/opinion/delicious-debrief-3.html) I looked at how I actually implemented those technical details.

After the low level technical stuff there was still a lot of work making it useful. That’s what I’d like to talk about today.

### But that’s not all

What I have been discussing so far has been entirely about the low-level, very technical details of OAuth. Of course there’s another side to it and that’s how it is presented to the user. This, again, has two parts: first, the options made available to the developer and, secondly, the work involved in actually making it happen.

So, the options available. We now have two authentication methods. I’ll call them Delicious and OAuth. The first point to make is that they’re not interchangeable. If I have an OAuth account I can’t log in with a Delicious username and password. And vice versa.

This begs the question: how can Yummy tell which type of account a user has?

The short answer is: it can’t.

Worse, many, if not most, Delicious.com users also have a Yahoo! account even when their delicious.com account is *not* linked to it. This results in a very confused user, as their login works without error yet they find they have no bookmarks.

What I was looking for was a way to identify the type of account that was accurate and would not require the same information to be entered multiple times. I ended up watching a number of people logging into their Yahoo! accounts ((Don’t worry, I wasn’t looking at what password you were typing.)) and, unfortunately, this invalidated most of my theories for making the process easier.

I thought, for example, that I was onto a winner when I noticed that I always typed “@yahoo.com” at the end of my username. Yummy could show the username screen as normal and, if the user typed “@yahoo.com” it would automatically remove the password field and offer to login using OAuth. However there are two problems with this. The minor, but annoying one, is that the user would be forced to enter their username twice, once in Yummy and then again in Safari. More significantly, I found that you don’t have to type “@yahoo.com” at the end of your Yahoo! ID. Although *I* do it all the time, most people seem to avoid the extra typing.

If people are going to avoid the extra typing, I would *still* need a way for them to override the default (Delicious) authentication method. And if they know that they have to overide it then, I reasoned, I may as well just come straight out and ask them how they’d like to proceed.

And this is exactly how it currently works.

[![](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2010/07/Welcome-OAuth-208x300.png?resize=208%2C300 "Yummy Log in Screen")](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2010/07/Welcome-OAuth.png)

Honestly, I’m really not very happy with it. How software talks to the server is entirely technical and is really not something that I should need to ask my users about. However this seems to be the least-bad approach. As I’ve noted before, I’m happy to entertain alternatives but I’ve not come across a better one yet.

The other significant user interface issue is one that I have already alluded to: should Yummy use a built-in web viewer or exit entirely and switch to Safari? The OAuth specification is clear on the matter: the users standard web browser should be used as it is both trusted and known ((We’re using an iPhone here so we can assume that the user is not using Internet Explorer.)). However, OAuth is really designed with web applications in mind. Even on a Mac this switch from “my” app to a web browser and back again would be far from ideal. But on an iPhone, that can only display a single application at a time, it is confusing at best.

All else being equal I would be happy to go against the advice of the specification and use an embedded web view if it made for a better user experience. Unfortunately, all else was not equal.

What I found was that, although I could log in correctly using the web view there was no way for Yummy to automatically regain control afterwards. If you’re familiar with OAuth you will be aware that there *is* supposed to be a method for doing this. I spent a long time trying to get this to work but never did. I’m unclear whether this was a problem in my code or on the Yahoo! side ((I’ve got this working in the development version of Yummy now. I’m still not sure where the problem was.)).

In practice, this would have meant that I’d have to provide instructions before the user was allowed to log in. Something like “press the ‘Done’ button when you have finished logging in and enter the code you were given.” Of course this is not dramatically better than copying the code from Safari and relaunching Yummy.

In the end I decided that I would completely follow the spec rather than not follow its advice *and* force my users to jump through a few hoops.

Again, this is not something that I am entirely happy with. Could I have implemented this differently? Absolutely! Would the user experience be better had I done so? Not significantly.

In addition to the big things there were also a number of smaller, more cosmetic difficulties.

There a few things that that Delicious.com API is not terribly good at. One of the problems I’ve had from day one is that it’s not really designed for applcations to synchronise bookmarks (which is kind of bizarre when you think about it). It can be done, but it’s pretty tricky, especially when you have limited memory as is the case on the iPhone.

The new Yahoo! ID authentication scheme brought another: how do you know who has just logged in? Previously the user entered their username, so Yummy would know immediately. However in this case, their username is entered into Safari and Yummy never sees it. It so happens that one API call does return the username, but only under certain conditions and not necessarily straight away.

I mention this not because it was impossible to solve — indeed it was not spectacularly hard — but because it was was unexpected. After working through the low-level technical details of OAuth; and after figuring out how to allow the user to exit Yummy and return to the same point (while still allowing the process to be cancelled); after all that, the process was still not complete. What appeared to be just a different username and password became a significant and fundamental change.

### Coming tomorrow

With most of the hard work finished I just had to [make sure it really worked](http://www.zx81.org.uk/computing/opinion/delicious-debrief-5.html), and then sit back and analyse what went wrong.