---
id: 140
title: 'Free Software HOWTO'
date: '2001-01-17T12:49:35+00:00'
author: 'Stephen Darlington'
excerpt: 'With the current Linux trend towards multi-million dollar IPO''s and "Open Source" software, much of the emphasis of "free" software has been lost leaving people new to the fold confused and not completely understanding all the implications. This HOWTO will, hopefully, reduce some of that confusion.'
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/linux/free-software-howto/free-software-howto.html'
permalink: /computing/linux/free-software-howto/free-software-howto.html
categories:
    - 'Free Software Howto'
tags:
    - books
    - business
    - Computing
    - development
    - microsoft
    - opensource
    - Opinion
    - Software
---

v1.2, 17 January 2001

With the current Linux trend towards multi-million dollar IPO’s and “Open Source” software, much of the emphasis of “free” software has been lost leaving people new to the fold confused and not completely understanding all the implications. This HOWTO will, hopefully, reduce some of that confusion.

### Introduction

**What’s in here?**

This document talks in non-technical terms about free software, what it means and why you should care about more than just the cost of your software.

**Who is this HOWTO for?**

People that have been hacking for years will already be fully *au fait* with the content of this document. Or at least you should be!

The Free Software HOWTO is aimed at people new to Linux, Open Source or free software.

**New versions of this document**

The official home of this HOWTO is [here](http://www.zx81.org.uk/computing/linux/free-software-howto/). You will always find the most up to date version here.

**Disclaimer**

You get what you pay for. I offer no warranty of any kind, implied or otherwise. I’ll help you where I can but legally you’re on your own.

**Credits and Thanks**

I welcome any constructive feedback on this HOWTO and any general software licencing issues, although my opinions are just that: a subjective view. You should understand what each licence means before committing to one for your own software or documentation..

**Licence**

This document is copyright 2000, 2001 Stephen Darlington. You may use, disseminate and reproduce it freely, provided you:

- Do not omit or alter this copyright notice.
- Do not omit or alter the version number and date.
- Do not omit or alter the document’s pointer to the current WWW version.
- Clearly mark any condensed, altered or versions as such.

These restrictions are intended to protect potential readers from stale or mangled versions. If you think you have a good case for an exception, ask me.

(This copyright notice has been lifted from Eric Raymond’s Distribution HOWTO.)

### Overview

**Introduction**

Until now, you’ve probably never given much thought to software licences. No-one can blame you. They’re usually pages and pages of legalese telling you what you can and can’t do with the CD you just bought. If you actually sat down and read it all, you would probably never agree to it!

Licences, however, are at the heart of what free or open-source software is all about. Let’s take a look at a number of very broad categories of licence.

**Commercial software**

The first type is the commercial licence, like the one that Microsoft or Lotus might insist you agree with before using their software. The basic premise is that you don’t own the software, you have an agreement with the author that allows you to use it within certain guidelines. As the copyright owner, they can impose whatever restrictions they want. Common conditions include limits on the number of concurrent users, number of copies, and what you can use it for (for example, “non-commercial use” or a ban on reverse engineering).

The emphasis is what you can’t do, and all the power is in their court!

One thing to note, and this will become more relevant later on, is that none of this relates to the cost of the software (or, more properly, the licence). You can get commercial software, such as Microsoft Internet Explorer, for no cost and still be forced to abide by the publishers conditions.

**Shareware**

The next kind of software, shareware, is sometimes called free, although as we shall see, that’s not correct.

Shareware was started in the early eighties by Jim Button when a few of his friends started passing round some software he’d written and he started getting phone calls asking for support. Eventually he added a request for $10 to the startup screen and shareware was born.

In short, shareware authors allow you to try out their software for free but request payment for continued use. Many of the same restrictions as for commercial software remain, including the limitations on reverse engineering, concurrent use of the full version, etc, stand. Additionally, the “free” downloads are often broken in some way, perhaps limited functionality or splash screens.

Interestingly, Linus Torvalds describes shareware as combining “the worst of commercial software (no source) with the worst of free software (no finishing touches).”

**Public Domain software**

All the licences we’ve seen until now have been designed to reduce people’s ability to do what they want with the software.

At the opposite extreme is public domain software. This is software that has no copyright and, therefore, no restrictions on its use. You can copy it onto as many machines as you like, reverse engineer it, make modifications and distribute it as you feel fit.

This is the first kind of software that we’re come across that can rightly be called “free.”

Normally, whenever you write something you automatically own the copyright, even if you don’t add an explicit copyright message. For public domain software, the author throws away these rights allowing everybody to do what they like with the software.

Unfortunately, “anything” also includes selling it. Imagine spending a huge amount of time producing your masterpiece, giving it away and then finding that someone else was able to sell it and make their fortune with all your hard work! Worse, people don’t even have to give you credit for your work; they can legally take it, replace their name with yours and distribute it.

This might be why there isn’t a huge amount on public domain software.

At this point it might be worth looking back at free commercial software. Both public domain software and a free piece of commercial software cost the same, but the freedom you’re given to use it varies. A common phrase you hear with free software is “think free speech not free beer.” The difference between public domain and commercial software show the opposite extremes.

**Free software**

By now it should be clear that there are many different kinds of free software and not all are equal. The version of free that this section relates to is the one promoted by Richard Stallman of the [Free Software Foundation](http://www.fsf.org).

But first, a little history.

The Free Software Foundation was formed in 1984 when a printer manufacturer refused to give Richard Stallman the source code (the computer instructions required to make a program). It had been leading up to this for some time — the increasing number of non-disclosure agreements, new software that banned sharing of information, etc. — and the printer manufacturer was just the straw that broke the camels back.

Stallman decided that he could not, in clear conscience, sign a non-disclosure agreement or work with a company that restricted his ability to share information. While most people would have given up at this point and gone to work, for obscene amounts of money, for a big company writing proprietary software, Stallman stuck by his principles and decided to make his own operating system, free of the constraints of commercial systems.

The process leading up to this is documented in more detail in Steven Levy’s excellent ‘Hackers.’ You’ll note that Levy calls Stallman ‘the last real hacker.’ Happily he was wrong, otherwise you wouldn’t be reading this!

As we can tell from the background, “free,” in this context, relates not to the initial cost but to freedom. Stallman was unwilling to surrender the right to make modifications or improvements to any software he used — and to do this you need the source code.

This may sound just like public domain software up to this point. The difference is that there are clauses in the licence that attempt to keep the software free no matter what changes are made. The most famous free software, Linux, uses the most famous free software licence, the GNU General Public Licence. It is sometimes also called Copyleft, as it very cleverly uses the current copyright laws to do the exact opposite of its original mandate.

The way it does this is by insisting that the code and anything derived from it is also released with the GPL licence. In some senses it is ‘viral’ in nature and it is this that is central to many people’s objections.

Also, it’s worth noting that the word ‘derived’ is a little too vague. Does a library linked to a GPL’d program need to be GPL’d also? Does a program running on a free operating system need to be GPL’d?

There’s no clear, obvious answer for either of these with the current version of the GPL. The new version (3) is intended to fix some of these shortcomings, but it’s viral nature will remain.

**Open Source software**

Open Source software is, in many ways, exactly the same as free software, despite what Richard Stallman says!

It was started in 1997 by Eric Raymond and Bruce Perens as a response to the increasing confusion over the use of the word “free” in relation to software. (Confusion that has continued, or I wouldn’t be writing this document!)

In essence, Open Source is a marketing or PR exercise to make free software more acceptable, more understood by the general public and the big corporates that, until that point, were comforted by the money they had to pay to get commercial software.

Like “free” software, the “Open Source” trade-mark does not mandate a single licence. (Freedom of choice is important, even when it comes to giving away software!) Technically any licence that meets all the requirements in the [Open Source Definition](http://www.opensource.org/osd.html) can be termed Open Source. These, in summary, are no restrictions on the use of the software, access to the source code and the freedom to make modifications and distribute them.

The two most famous are the Berkeley System Distribution (BSD) Licence, which allows distribution without the source code, and the GNU General Public Licence, although there are many more.

The [Sun Community Source Licence](http://www.sun.com/981208/scsl/principles.html), for example, is not compliant because Sun Microsystems demand a fee for any commercial distribution and insists that derivations are still compatible in some arbitrary ways. (This is not intended to single out the SCSL as being particularly bad. However, the fact that it purports to be “open” when it isn’t is a disturbing trend.)

### The implications

**Overview**

Free software has already had a significant effect on the computer industry. Free software is behind most of the critical parts of the Internet, it was used (unsuccessfully) as part of the defense in the Microsoft anti-trust trial and the spate of recent IPO’s has shown that there’s money too.

Unless you bought some shares, this all appears to be affecting other people. There is an impact, however.

**I just use software, how does this all affect me?**

It’s tempting to think that, if you’re not a ‘techie’ or a hacker, the difference between free commercial, public domain and Open Source software is minimal. But that’s not true, even as a user the difference affects you because the development of the software is affected.

I’ll outline a plausible scenario as an example.

Company X designs and releases a fantastic piece of software. It’s commercial software, but the publisher seems receptive to new ideas, indeed versions 1.1 and 2.0 are exactly what you were looking for and the upgrade costs were reasonable.

At this point any number of things can happen. Perhaps you find a bug in it, one critical to your business. But the publisher offers no warranty for the software and say they are not sure whether they will fix it. (Note that just because you paid for the software, you do not necessarily get better service or a guarantee of any kind. According to the licence, you can’t sue Company X if the software is not fit for the purpose it was sold for.)

Or maybe they go out of business. Or perhaps they start competing with your company and won’t sell you the next version. Or perhaps the features you want are not in the new version. There are a huge number of ‘if’s and ‘maybe’s, all outside your control.

Basically, if you use commercial, close-source software you are at the whim of the publisher. If they do something you don’t like, tough.

However, if you’d used Open Source software you’d have access to the source code and could fix or upgrade the program as *you* saw fit. And if you couldn’t do it, there are many programmers willing to support the new versions or you could hire someone to do it for you. In summary, you have much more control over future development of the product.

You’ll note that none of the advantages here are strictly related to cost. I think that’s something that people tend to focus on too much, possible due to the “free software” title. However, there are still advantages.

But first we need to get away from the initial cost of the software as that’s normally a small percentage of the total cost. Instead, let’s think in terms of support costs. Once you’ve installed the software, what costs are there? An obvious cost is that of upgrades. Less obvious is lost productivity due to software failure and support charges from the manufacturer.

In the case of free software, there are no upgrade costs (other than the time and inconvenience of doing it, which also applies to commercial software). Free software is usually regarded as more reliable then commercial software — see [Fuzz Revisited](http://www.cs.wisc.edu/~bart/fuzz/fuzz.html) for more information. And the support charges are optional: you can either deal with it in-house or hire any one of a number of support organisations.

**I’m a developer. How does this affect me?**

As a developer, you’ll already know the benefits of being able to access the source code for a program. You can fix it, see how it works and integrate bits of it into your new program. (Using parts of another program, however, isn’t quite that simple and is dependent on the licence of the original software.)

A common problem developers see is the loss of their livelihood. If everyone gives away their software, how can anyone make money? It’s a fair question and there’s no single, correct answer.

Perhaps the most common answer is that most software is developed in-house and is not distributed. None of this development will be affected, so if you have that kind of job you can rely on your salary for a while yet!

If you work for a consultancy, almost all the revenue comes not from selling software but from “professional services,” i.e., they charge for developing the software rather than the licence to use it. Again your job is safe.

Then there’s shrink-wrapped software. The Free Software Foundation would say that it should be free. So if you listen to them and you work for Microsoft your job is in danger unless they diversify into services.

The Open Source people would say that there’s nothing wrong with shrink-wrapped software, but point out that there are advantages in releasing the source.

As you can probably see, the risk to your jobs is small and there are many benefits. At least that’s the way I see it and I work writing software!

**Where can I read more?**

The most obvious place to read more is at the [GNU website](http://www.gnu.org), after all they started it all.

But there are alternatives. Other important web-sites are as follows:

- [Open Source](http://www.opensource.org). This is the ‘official’ Open Source page. There’s lots of interesting stuff here, including a more detailed discussion on the effect of free software on different people Microsoft’s Halloween documents, their unofficial response to the Linux threat.
- [Eric Raymond’s web-site](http://www.catb.org/esr/). Eric has written much about Open Source software, with much more depth and style than I can muster!
- [Slashdot](http://slashdot.org). There aren’t more ‘HOWTO’s here, but Slashdot is a community of people interested in Open Source software. The discussions sometimes get childish, but you can learn a lot!

There are also a few books published (at least partially) on the subject:

- [OpenSources. Voices from the Open Source Revolution.](http://www.amazon.com/exec/obidos/ASIN/1565925823/zx81orguk00). This book talks about all aspects of the Open Source community, including licencing. The main reference is Bruce Perens essay.
- [The Cathedral and the Bazaar](http://www.amazon.com/exec/obidos/ASIN/1565927249/zx81orguk00). Again, this book is about general Open Source issues, but it includes a discussion on some of the non-obvious implications of the licences, particularly the reason why just because you can, you don’t frequently get many versions of a piece of software.
- [Hackers](http://www.amazon.com/exec/obidos/ASIN/0385312105/zx81orguk00) Steven Levy talks about the early days of the hacker community, including a good piece on Richard Stallman.