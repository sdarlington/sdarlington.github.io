---
id: 41
title: 'What About Free Documentation?'
date: '2002-10-19T17:23:02+01:00'
author: 'Stephen Darlington'
excerpt: 'The minster and the market? '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/opinion/what-about-free-documentation.html'
permalink: /computing/opinion/freedocumentation.html
categories:
    - Opinion
tags:
    - Computing
    - Opinion
---

**Introduction**

There’s a lot of free or open source software on the net, and much been written about both that software and the process that drives it. [Eric Raymond](http://www.catb.org/esr/), of course, is currently the main anthropologist although Steven Levy beat him to it and there are many others.

There is also a significant amount of free documentation. One only needs to take a look at [the GNU web site](http://www.gnu.org) (their definition of a free operating system includes free documentation) or the [Linux Documentation Project](http://www.tldp.org) to see that. However, there doesn’t seem to have been a “Cathedral and the Bazaar” for free documentation, or even anything similar.

That’s kind of what I want to do here, but I’m not going to go into as much detail. Instead, I’m going to write about my own experience writing free documentation (my [Oracle 8i Installation Howto](/computing/oracle/oracle-howto/)), the trial and tribulations, the ups and downs, the good times and the bad… You get the idea.

**Starting off**

I guess the first thing to note is that I *didn’t* write the HOWTO to ‘scratch an itch’ — I already knew how to install Oracle! Instead, I noticed that many people were having difficulties and that I was spending quite some time replying to the same questions on newsgroups and Oracle Technet. You could say that I wrote the document in order to be just as helpful but without being quite so intensive on my time! (So my itch could have been to save time.)

Another motivator was ‘to put something back into the community.’ Sounds a little pretentious, but it’s true. I’ve been using Linux since 1994 and, although an able developer, have never contributed any code to any free software. This was my chance! I suppose I naively thought that writing English would also take less time than C. As we’ll see later, that didn’t turn out to be the case.

I think that this is an important difference between free software and free documentation. No-one will ever write free documentation to “scratch an itch” (as Eric Raymond so eloquently put it). This takes away, quite possibly, the greatest incentive to create something and may explain why, generally speaking, text is very much a second class citizen to code.

**Release early; release often**

The first decision I really needed to make was tools to use. My first thought was to add a few new pages to the web site that you’re currently reading. And then I got lazy. I decided to base my new work on the then current Oracle HOWTO, which meant that I had to get to grips with SGML and the SGML-Tools programs. At this point I wasn’t thinking in terms of getting it into the [Linux Documentation Project](http://www.tldp.org/), I just wanted to get a head-start. Once I’d actually started, it didn’t take me long to figure out that the structure of the old document didn’t match what I needed and, more or less, started again from scratch. I did, however, keep the same tools.

Having just read the [Cathedral and the Bazaar](http://www.amazon.co.uk/exec/obidos/ASIN/1565927249/zx81orguk), I consciously decided to issue my document before it was complete. I quickly wrote the introduction, prerequisites and installation sections and added a number of place-holders for the remaining sections. I then announced it in a message to Oracle Technet and a couple of newgroups.

Very quickly I got some excellent feedback. People were asking for clarifications and new questions, and others were pointing out factual errors. As with software, I quickly added these fixes and thanked the contributers both by email and in the document itself.

I was very pleased that this approach worked. Normally I would have ‘finished’ my work before making any issue, but by releasing early I was able to help more people early on *and* elicit — I’m guessing here — more useful comments. (I figure that’s true because I think I’d be less inclined to contribute to a finished document than a work-in-progress.)

**Maintenance**

Around version 1.5, a couple of weeks after my initial release, it was more-or-less complete. All sections were filled in and I managed to complete a successful installation just by following the steps I’d written about.

The first issue was the people didn’t follow my advice — how dare they! Oracle is a big and complicated application and, even on Solaris, you just don’t change things unless you have to and you always use a ‘certified’ operating system. This is an alien mind-set to many Linux developers, who tend to thing “newer is better” and is not helped by all the weird and wonderful devices that you can connect to an Intel-based PC.

The first questions I received that deliberately weren’t answered in the HOWTO were problems with different distributions. People were trying to get Oracle running on just about anything with a Linux kernel!

I didn’t fancy wiping my PC clean and attempting the install with as many different distributions as I could find, I just didn’t have the time. Fortunately, the same community on the Internet that helped me complete my first version added to my knowledge base.

I started to add more and more detail to the HOWTO. If you’re using RH6 do this, with Debian do that… It seriously affected the “flow” of the document for everyone. Given my Oracle (conservative) background, this is just not a problem I originally considered.

When Oracle released 8.1.6 I made the decision that the HOWTO was for RH6 and Oracle 8i R1. It would make the occasional nod to later releases of both the database and the distribution, but fundamentally the focus would be on one version of Oracle and one version of Linux.

As a kind of half-way-house, I started to add extra pages to my website detailing some of the idiosyncrasies of different Linux distributions or newer versions of Oracle. I’m still not completely happy with this approach but I’ve not heard of a better solution yet.

**Feedback**

Having “completed” my document, what keeps me editing? If I’m writing software, my motivation is adding cool new features. Or maybe adding new stuff for other people and waiting for their praise?

As I mentioned earlier, things are very different for documentation writers.

I’ve got an awful lot of mail about Oracle and Linux since late 1999 when I first published the HOWTO. The email I get seems to have gone through a number of phases. When I first issued the document, I got an almost fifty-fifty split between “thank yous” and suggestions for improvement. Almost all was positive, constructive and friendly.

Without it I would almost certainly have stopped writing. At this point I suppose my motivation was to increase the ratio of thanks to suggestions. I turned a stream of emails into a challenge!

As the HOWTO started to get into wide circulation, the number of helpful suggestions started to drop and the number of questions started to rise dramatically. Some I saw as suggestions as I didn’t cover those details, but most were just from people who clearly couldn’t be bothered to read any further than the front page and my email address.

I can’t count the number of messages I’ve received saying “it didn’t work, what should I do?” (in as many words). How should I reply to that without being rude?! I’ve also received emails from people giving me their “root” password and other confidential details.

The next stage was when Oracle released a newer version and RedHat decided to go with a new version of GLIBC for version 7 of their distribution.

By this point, my motivation was mainly trying to reduce the number of messages I was receiving. Sure, I *felt* like being rude but I rarely was. I tried to answer all the most common questions in the document, but this point was definitely the low point. Although the updates were helpful, I was doing them for the “wrong” reasons, and the number of messages saying “thanks” had dropped to virtually zero.

More recently I’m only getting the occasional question. It’s difficult to know whether that’s because my HOWTO covers just about everything it needs to or because I’m just not promoting it as much as I used to or because the cutting edge in Oracle is now with 9i. Or maybe I *was* rude and people are too scared to talk to me..?

**In conclusion…**

If my original intention was to save time, it failed miserably. I’ve spend even more time replying to emails and maintaining the document than I would have done occasionally adding comments to discussion groups.

Towards the end of this piece I’m sounding very negative, but that’s a bad way to finish as generally speaking it has been very enjoyable. Getting a Linux distribution with your work on is quite a buzz and it’s always nice to get a friendly message or offers of free CDs and books from strangers.