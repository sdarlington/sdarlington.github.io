---
id: 4611
title: 'What do you know?'
date: '2017-08-14T21:17:35+01:00'
author: 'Stephen Darlington'
excerpt: 'How do you interview people for technical roles? Should you ask questions about algorithms?'
layout: post
guid: 'https://www.zx81.org.uk/?p=4611'
aliases: ['/computing/opinion/what-do-you-know.html']
categories:
    - Opinion
tags:
    - development
    - interviews
    - people
    - technology
    - work
---

How do you interview people for developer and technical jobs? This is an enduring question, and one with many angry factions.

It’s too big a subject to tackle in its entirety and I have no intention of trying. Instead, I want to talk about one aspect: should you ask Computer Science questions or not?

In one corner are the people who argue that you never need to implement a linked list or write Quick Sort in real life, so asking you to do that in an interview is unreasonable and excludes good candidates. They argue that there are more important things to consider, such as the use of applications frameworks or design or working with other people.

In the other are those who say that algorithms are a fundamental part of writing software and, while you may not need to write a Quick Sort, you *do* need to understand it and to be able to explain it.

The first group calls the second elitist. The second calls the first naive. Who’s right?

Of course, I come at this with my own bias. I have a Computer Science degree but I did it some time ago and don’t have perfect recall on this stuff. Ask me the [Big O notation](https://en.wikipedia.org/wiki/Big_O_notation) for [Quick Sort](https://en.wikipedia.org/wiki/Quicksort) and I’ll understand the question and maybe make a stab at the answer, but I’m not going to pretend I’m 100% sure.

There are two main angles I want to consider: the intent of the interviewer; and the knowledge a developer actually needs to do the job.

Let’s start with the former.

So, your interviewer asks you to implement a linked list on a whiteboard. Why? What are they hoping to find out about you?

If the answer is… well, the answer, then I’m very firmly with the “you don’t need to know this stuff” crowd. People tend to want a specific answer when either they want a cookie cutter computer science graduate or they wouldn’t understand the answer.

Alternatively they might be trying to see how you think; how you’d start with a simple solution and build up; how you’d test it. In these cases, the answer is less important than how you got there.

Another thing to consider is that, as an interviewer, you want to get the most information in the least amount of time. Starting with a “real” business problem might require too much context to be explained before you could really start. But the candidate hopefully already know what a linked list does, even if they’ve never had to write one.

Of course, sat in a conference room with a stranger it’s very hard to tell which of the two camps your interviewer falls into (and practically impossible if they’re on the phone).

So that’s pretty inconclusive. There *are* good reasons to ask but you can’t tell whether that’s the case for your interviewer.

So how about job requirements?

This angle is easier. Most jobs *don’t* require standard algorithms that you’d come across in a computer science or software engineering degree. A knowledge of user interface frameworks probably *is* more useful for many projects.

But what about the rest? There *are* jobs where knowing algorithms is important. On projects where low-level or performance intensive code is required understanding the fundamentals can be important. Maybe you’ll be writing a game or something with very low latency requirements or an engine that processes vast amounts of data.

In my last project I deliberately avoided using the system provided Quick Sort and implemented my own Heap Sort. I may not have been able to tell you the Big O notation for heap sort and quick sort, but I *do* know that quick sorts’ Achilles heel is that it works poorly on already sorted data. (It’s only fair to note that they *didn’t* ask me about algorithms when I interviewed for that position. In fact, they didn’t ask me much of anything! That’s a long story for another time.)

I’m not saying that you need a Computer Science degree to know those things. I’m not saying that the project would have failed without that background (though the fact that *someone* knew saved tens of thousands of pounds in hardware costs). And, most importantly, I’m not saying that the kinds of projects that you do are anything like mine. I *am* saying that the people who say this stuff isn’t useful or important are wrong.

So what do we conclude?

Well, firstly, and most importantly, no one size fits all. Your interview process needs to be tuned for the kinds of position you’re trying to fill.

Secondly, if the *only* questions are about linked lists and sort algorithms, that’s a big red flag. These aren’t the only interesting subjects for *any* job. If you’re not at least asked about how you work in teams, you should be worried.

Finally, having said all that, you can’t escape from the fact that programming *is* about algorithms. [According to Wikipedia](https://en.wikipedia.org/wiki/Computer_programming):

> Programming involves activities such as analysis, developing understanding, generating algorithms

You *should* be expected to understand and to be able to explain algorithms.

But you should also understand team work, several programming languages, relevant frameworks, user interface design, source control, your IDE, the Unix command line, security, Linux, web servers, leadership and management, the film that the line “pop quiz, hotshot” comes from and know the correct answers to “tabs or spaces?” Developing software is hard and has many facets.

Focusing on any one aspect to the exclusion of others is a mistake. And that’s true both for you as an individual and you as an employer.