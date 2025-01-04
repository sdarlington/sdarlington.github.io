---
id: 54
title: 'Oracle PL/SQL Programming'
date: '2002-10-19T18:34:37+01:00'
author: 'Stephen Darlington'
excerpt: 'Having recommended it in my Oracle for Linux Installation HOWTO, I thought it was time I documented why I value it so highly. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/opinion/oracle-plsql-programming.html'
permalink: /computing/opinion/plsqlprogramming.html
categories:
    - Opinion
tags:
    - books
    - Computing
    - Opinion
    - Programming
    - review
---

**Introduction**

<iframe align="left" frameborder="0" marginheight="0" marginwidth="0" scrolling="no" src="http://rcm.amazon.com/e/cm?t=zx81orguk00&o=1&p=8&l=as1&asins=0596009771&fc1=000000&IS2=1&lt1=_blank&lc1=0000ff&bc1=000000&bg1=ffffff&f=ifr" style="width:120px;height:240px;"></iframe>The first point to note is that this book is published by O’Reilly. The second point would be that Steven Feuerstein is generally regarded to be one of the worlds leading PL/SQL experts.

Those two point, on their own, were enough to clinch the purchase just over eighteen months ago.

**Content**

The book is, to say the least, comprehensive. When I first started to use PL/SQL I would never have guessed that there was enough there to write a thousand page book, but there is.

It’s split into seven sections and twenty-six chapters, making it a good reference as well as useful to learn from. Section one, ‘Programming in PL/SQL’ talks about the history, block structure and style. I’m not entirely convinced that ‘programming style’ belongs in a book such as this, but it’s well written, useful and less intrusive than the similar treatment in “[Practical C](practicalc.html).”

Section two moves onto the ‘meat’ of the language and takes up over two-hundred pages in its own right — longer than the whole of some other texts! Feuerstein covers all this in detail and with great skill, mentioning not only how the language works but also, where appropriate, where it doesn’t work. This kind of honesty seems rare, especially in Oracle Press books!

‘Built-in Functions’ does exactly what you’d expect, and includes a thorough discussion on handling dates, a common area of confusion (I was pleased to find that it’s not just me…).

Parts four and five are, perhaps, the most clumsy sections. The first talks of ‘Modular Code,’ which I don’t see as being so advanced that it requires its own section. And part five discusses the ‘New PL/SQL8 Features’ which, again, don’t necessarily deserve a section on their own. I suppose it made writing the second edition easier…

The last section before the appendices is called ‘Making PL/SQL Programs Work.’ For those not familiar with server-side PL/SQL, let me point out that this isn’t as silly as it sounds. PL/SQL, until recently, had no debugging facilities to speak of. You can’t set break-points or single-step and even outputting trace statements to the screen is not trivial.

However, although the stuff that Feuerstein writes is interesting and might be useful to some, it’s not all it might be. For example, in the section on tracing PL/SQL programs (chapter 26) he talks about *Oracle* tracing which, if you’ve ever seen, you’ll realise how useless it is much of the time. (If you’ve not seen it before, be warned that you’ll get thousands of lines of very low-level junk for even a simple program.)

Why did he not talk about a tracing library, say, that logs trace messages into the database with a pipe? I ended up writing one myself, based on the information in the book but I’d preferred not to have!

**I thought you said you liked it?**

If you said that the last section was very negative I wouldn’t be able to disagree with you. However, this is a book that I’ve been using for over a year, not something I got as a review copy and skimmed. I’m still using the book on a daily basis so it must have some merit. I would never have found many of the problems if the book hadn’t been an important and useful reference for all this time.

O’Reilly know how to publish a good technical book. They focus on telling you what you need to know and how it does, should or, indeed, does not work. Feuerstein’s *Oracle PL/SQL Programming* is one of the better O’Reilly books, so you should be able to guess how highly I rate it.

I first got my copy over a year ago and I’ve spent most of that time on Oracle projects. I have kept this book by my side at all times and only on a few occasions has it not been able to answer my questions. It’s now so well used and grubby that I may be forced to buy a new copy.

**The facts**

Author: Steven Feuerstein with Bill Pribyl

Cost: $46.95

ISBN: 1-56592-335-9

Buy this book from [Amazon.com](http://www.amazon.com/exec/obidos/ASIN/1565923359/zx81orguk00) or from [Amazon.co.uk](http://www.amazon.co.uk/exec/obidos/ASIN/1565923359/zx81orguk).