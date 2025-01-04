---
id: 73574
title: 'Is git too hard'
date: '2022-09-06T17:03:00+01:00'
author: 'Stephen Darlington'
excerpt: 'We need to be careful not to throw the baby out with the bath water when we critique git.'
layout: post
guid: 'https://www.zx81.org.uk/?p=73574'
permalink: /computing/opinion/is-git-too-hard.html
categories:
    - Opinion
tags:
    - coding
    - development
    - opensource
    - Opinion
    - process
---

<span style="font-size: revert;">I stumbled across “</span>[On git and cognitive load](https://dzone.com/articles/on-git-and-cognitive-load?edition=519297)<span style="font-size: revert;">” and it got me thinking. That post led me to “</span>[Oh shit, git!?!](https://ohshitgit.com)<span style="font-size: revert;">” and that got me thinking further.</span>

But first, a disclaimer: this is a post more about having perspective than providing answers. If I knew a better way, I’d be doing it.

The first blog argues that git is difficult to use. Further, that it was designed with the limitations of the time and that those limitations are no longer valid constraints. A decentralised system was required when poor network connections were the norm. Now we have cloud providers and ridiculous amounts of bandwidth.

The second post notes that people keep getting themselves into a bind, with some helpful tips on extricating yourself from those situations.

The fun thing to note here is the kinds of problems that we need to solve with git:

- I missed a file from a commit
- I put the wrong commit message
- I put committed a change on the wrong branch
- I need to remove a commit

To me, the fascinating thing about all of these things is that in the systems that came before git, *it wasn’t possible to do any of them*. Once you made a commit in [Subversion](https://subversion.apache.org), that was it. It was in the repository and immutable<sup>[1](#fn1-14229 "see footnote")</sup>.

Missed a file from a commit? *Shrug*

Committed something you shouldn’t have? *Tough*<sup>[2](#fn2-14229 "see footnote")</sup>

Also, in the late 2000s, when git was just starting to take off, an argument *against* switching was that the commit history was not sacrosanct; the record could be changed. Subversion’s behaviour was a feature not a bug.

In the next decade, we’ve changed mindset so much that the ability to change a commit is now expected, even when we know that it can cause problems.

Similarly, while git’s distributed nature certainly adds to its complexity, it’s both fantastically useful and not a source of its worst behaviours. I can sit on a plane with no internet access and still have most features. I can move my repo between cloud providers or host my own. When my broadband or AWS goes down, I can continue working.

Maybe rather than move to a [proprietary, cloud-based source control system](https://www.diversion.dev) — which is what the author of the first piece is really advocating — we should remember [what we gained when we moved last time](https://twitter.com/quinnypig/status/1508593001844510725?s=21&t=NcOmFocDTeTzpYA9ge_H7g).

Git *is* tricky. But rather than return to a centralised system maybe we should fix git’s user interface. Being able to fix past commits is useful, though we we should be able to do so without messing up our code or, especially, the code repository.

<div class="footnotes">---

1. As ever, it was always possible to hack the repo but in my experience this was frowned upon. [↩︎](#fnr1-14229 "return to article")
2. I do remember a time when someone committed a password. It took a lot of time and expertise to scrub it from the history. [↩︎](#fnr2-14229 "return to article")

</div>