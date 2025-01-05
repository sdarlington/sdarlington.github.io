---
id: 1688
title: 'Snow Leopard'
date: '2009-09-16T20:11:41+01:00'
author: 'Stephen Darlington'
excerpt: 'Early impressions of Apple''s new operating system.'
layout: post
guid: 'http://www.zx81.org.uk/?p=1688'
aliases: ['/computing/opinion/snow-leopard.html']
categories:
    - Opinion
tags:
    - apple
    - Computing
    - mac
    - review
---

Most people reading this will know that Snow Leopard refers to version 10.6 of the Macintosh Operating System, Apple’s latest update released late last month.

I wasn’t sure whether I should upgrade initially. I have been stung before by being an early adopter. Mac OS X 10.4 was a nightmare on my iMac G5. The big ticket new features such as Dashboard and Spotlight worked just fine[^1]. What didn’t work were little thing like, oh, networking. Eight times out of ten it couldn’t connect to my AirPort Base station. This made almost everything, including downloading patches to fix this very problem, a compete and utter pain. I think it took until 10.4.3 before everything worked reliably.

I waited several months before making the leap to 10.5 for this very reason. But Leopard at least had some neat new features (and the lame new look of the dock) to try to tempt me over. Snow Leopard, by design, has few user-facing enhancements to make it worth the risk.

Of course I’m not a typical end user. [The reason I moved from Windows to the Mac](http://www.zx81.org.uk/computing/opinion/dreadfulthought.html) back in 2001 was because of its Unix underpinnings:

> MacOS X is based on a BSD Unix kernel (called Darwin and available under an Open Source licence) and has an enhanced Macintosh user interface grafted on top. This is truly the key. You have the complex internals available from a command-line when you need it and a state of the art GUI when you just need a word processor.

And now that [I’m an iPhone developer](http://www.zx81.org.uk/software/) I have a vested interest in using the best tools available for the platform, and they were only available for Snow Leopard. Also a lure where the new APIs ([Grand Central Dispatch](http://developer.apple.com/mac/library/documentation/Performance/Reference/GCD_libdispatch_Ref/index.html), [OpenCL](http://developer.apple.com/mac/library/documentation/Performance/Conceptual/OpenCL_MacProgGuide/Introduction/Introduction.html)) and language enhancements ([blocks](http://developer.apple.com/mac/articles/cocoa/introblocksgcd.html)). I’ve not done much Macintosh development but these were exactly the kind of things that would potentially get me started.

All this is a long way of saying that, despite the risks, I took the plunge anyway.

And…

Well, so far it’s pretty much been a non-event.

Yes, it’s quicker. Most noticeably in starting up, shutting down, Time Machine and in Mail. Don’t get me wrong, there are lots of nice little things — and I’m still finding new ones — but it’s mostly been entirely seamless, almost an invisible upgrade. And I mean that in a good way.

Yes, all my programs still work. I’d read reports that PhotoShop Elements didn’t work under Snow Leopard. I can report that it takes a considerable amount of time to start up and frequently beach-balls afterwards. Or, put another way, it works just as well as it did under 10.5.

I’d also seen scare-stories about old versions of Microsoft Office and other PPC applications that need Rosetta to run but, again, I’ve not seen any problems[^2]. Even lower level software like my screen calibration program and [film scanner software](http://www.zx81.org.uk/computing/opinion/dualscanii.html) are fine.

I have two negatives so far, both fairly minor in the grand scheme of things.

The first affects [Yummy and Yummy Browser](http://www.yummyapp.com/) and that’s the fact that the new version of Xcode only supports developing for iPhone OS 3.x[^3]. Luckily there are very few users on 2.x but it’s still a little disappointing that I have had to make the move.

Secondly, it’s my printer. There is no longer a HP-supplied driver for my 2002-era DeskJet. Luckily Apple includes GutenPrint with Snow Leopard and there’s a bundled driver that recognises it. So on the plus-side I don’t have to go out and buy a new printer as I feared I might have to. On the down side the quality is just not there. While it was never a match for any contemporary photo printer, it was more than adequate for my needs. With GutenPrint, text is readable but there’s noticeable banding. I’m not sure I’d use it any more for “official” letters, though maybe I’m just being a snob. Photos have the same issue with banding but have the added distraction of some coarse dappling as a substitute for the more subtle colours.

No significant upgrade is going to be entirely problem-free but overall I’m happy with it. It’s about as easy as it could be and, despite Apple’s claim of no new features, there are certainly tangible benefits to making the leap.
[^1]: Some would argue with that statement. Personally I never had any serious problems with Spotlight.
[^2]: To be fair, I moved to Office 2008 around the same time.
[^3]: It’s true that you can build for older releases but there’s no way to test it in the simulator. I’m not willing to release software that I’ve not been able to test.
