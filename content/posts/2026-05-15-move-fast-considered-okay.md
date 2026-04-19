---
date: '2026-05-15T10:34:03+01:00'
title: 'Move Fast And Break Things Considered... Okay?'
author: 'Stephen Darlington'
layout: post
categories:
    - Opinion
tags:
    - software
    - development
    - meta
    - facebook
---
“Move fast and break things” has gone from a cool phrase to believe in to the process boogie-man. It’s become so mainstream that it’s used to [describe politics](https://om.co/2026/01/21/velocity-is-the-new-authority-heres-why/). It’s now the underlying problem to many of Silicon Valley’s biggest companies. Except... is it?

The phrase is originally [attributed to Mark Zuckerberg and Facebook](https://en.wikipedia.org/wiki/Meta_Platforms#History), and the fact that I appear to be defending him hurts me deeply. Honestly, I would prefer it if I didn’t.

Anyway, “move fast and break things” is not _necessarily_ a bad idea. Rather, it’s situational.

Here’s a story. I worked for a large company a number of years ago. They swung wildly from one extreme of the process spectrum to the other. One year, they would... move fast. There would be little process and people would end up live-editing code on the production servers.

This would be great. They got a lot done in a short period of time. The end users were happy, because they got their wishes implemented in next-to-no time. It was amazing.

At some point, things would, inevitably, break. Often in some minor way. Other times in dramatic, system down kind of way.

Did I say that this was a bank, and that the dramatic way could, literally, mean the loss of millions of Dollars?

After these events, they’d swing to the other end of the spectrum, adding so much process that nothing much could happen. No mistakes, but no flexibility and a huge loss of velocity.

So, what is the correct amount of process? [_It depends_](/posts/2025-02-14-it-depends/). If you’re a growing social media web site, it probably _is_ a reasonable compromise to risk occasional breakage (or even data loss) in exchange for faster iterations and more features. There was a _reputational_ risk to being down[^friendster] but there wasn’t even a real cost until they started adding advertising.

But you don’t want that same attitude for the brakes in your car, a nuclear power station, or the fly-by-wire code in an airliner.

Most software we use doesn’t fall at either of those extremes. The risk-reward calculations are different for every business and every application. Each company has a different tolerance for risk and different odds for each of those risks manifesting. The complexity of the application, the experience of the team, the stability of the tooling, the frequency of changes, the effects of errors... there are _many_ factors.

Ultimately, what people mean when they say that “move fast and break things” is bad is that the calculation for this particular tool is perceived to be incorrect. That’s a mouthful because there’s not one correct answer. If you’re Facebook _now_, you can afford to [make things worse for users](https://en.wikipedia.org/wiki/Enshittification) because... where else can they go? If you’re Tesla, maybe more quality and less breakage should be higher on your list of priorities.

Breaking things is never the goal. Software is so complicated that it will happen sooner-or-later no matter how careful you are. But the key is that it’s choice. Let’s make sure we’re making the right choices.

[^friendster]: It’s difficult to remember these days, but the competition in the early days were Friendster and My Space. The former, especially, had serious stability and performance problems. It’s not the only thing that killed it, but it’s absolutely a factor.