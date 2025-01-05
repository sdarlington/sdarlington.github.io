---
id: 313
title: 'Blessed is the Tool Maker'
date: '2007-04-05T19:10:54+01:00'
author: 'Stephen Darlington'
excerpt: 'Is writing software tools the thing that make some developers significantly more productive than others?'
layout: post
guid: 'http://www.zx81.org.uk/computing/opinion/blessed-is-the-tool-maker.html'
aliases: ['/computing/opinion/blessed-is-the-tool-maker.html']
adman_disable:
    - 'on'
categories:
    - Opinion
tags:
    - Computing
    - developing
    - mac
    - Opinion
    - people
    - Programming
    - Software
---

In the fifth part of Douglas Adams’ Hitchhiker trilogy, Arthur Dent makes his living among a group of stone-age settlers by utilising the one skill he had that was relevant to that world: sandwich making.

I guess we all have a special skill. But my point in this article is that if you’re a software professional, your special skill (unless you’re stranded on a stone-age planet) should be making software tools.

This realisation dawned on me over a long time. It’s well known that developers range in ability by at least an order of magnitude but less clear why. I’m certainly not qualified to answer that question in its entirety, however I’m convinced that developers can punch well over their weight simply by learning to write software that automates dull tasks, such as writing other programs.

Now a lot of people reading this will be thinking, “What’s the big deal?” Is this not obvious? Does every developer not do this? Originally I thought they did but recently became clear to me that that is not the case.

As is my habit, I had written a small utility program. A colleague was going through the same problem so I shared it with him. Even if we didn’t work for the same company, the script had only taken me a couple of hours to write. I made no claims that it was perfect but I knew that it did most of the heavy lifting required.

Next came the surprise.

A couple days later I conversationally asked how he’d got on with my script. It turns out that it didn’t work straight away; there was a minor bug. As far as I can tell he immediately abandoned my code and spent five hours doing the same thing by hand. He’d not mentioned the bug to me before and, for the record, it took about ten minutes for me to fix the problem that he’d encountered.

So, let’s make things very clear here. This otherwise smart person had done five hours work rather than spend a few minutes looking through a program or, even more bafflingly, ask me a simple question[^1].

What’s the difference? Why do some people go out of their way to write simple programs while others go out of their way to do repetitive, mind-numbing tasks?

I think it’s simple. Writing a program to write another program just does not occur to many people, they have difficulty thinking in abstract terms and, in general, can’t go “meta.”

Looking back to my university days I remember a number of parallels. A number of people had problems with the assembler course, but the most telling in many ways was on our compilers course. A compiler is a literally a program that writes another program, normally from a high level language such as C++ to assembler or machine code, and to do this you need to keep two separate worlds in your head simultaneously. Firstly you need to consider the program that you’re writing, that is you need to remember all the lexical tokens and the grammar as well as the memory you’re allocating and using. Secondly, you need to keep track of what’s going on in the program that the compiler will be writing when it runs, stuff like the stack, the memory that it will need to allocate at run-time. Since both are just computer programs, many, if not most, of the people on the course had some difficulty getting their head around either the concept or at some level of the implementation.

So far you might think that I’m bragging, but really I’m not. There’s another key part of this. It’s not just a matter of building software tools, it’s knowing when it’s not worth the effort. Had my colleague known that it would take me five hours to fix the problem then he would have made the right move (if we discount the possibility that the script could help other people if fixed).

Similarly, on a number of occasions I have spent far longer building a tool than it would have taken to do it by hand. Sometimes the desire to solve a programming challenge means that I lack the perspective to see when it’s not such a good idea to script the task. Tool building is not without risk. Those truly great developers, no doubt, have both the tool building ability *and* the ability to recognise when it makes sense to do so.

But overall I still think that one very significant factor in making some developers more productive than others is their ability to write software tools, particularly programs that write other programs.
[^1]: There’s an argument that the problem here is his communication skills. I’m not convinced that is the case in this circumstance. He’s normally fine. And I think I’m fairly approachable!
