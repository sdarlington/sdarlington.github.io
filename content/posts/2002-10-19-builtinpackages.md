---
id: 33
title: 'Oracle Builtin Packages'
date: '2002-10-19T17:23:02+01:00'
author: 'Stephen Darlington'
excerpt: 'A perfect accompaniment to ''Oracle PL/SQL Programming'' or should it have been included in the original? Stephen Darlington finds out. '
layout: post
guid: 'http://www.zx81.org.uk/computing/opinion/builtinpackages.html'
permalink: /computing/opinion/builtinpackages.html
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
<iframe align="left" frameborder="0" marginheight="0" marginwidth="0" scrolling="no" src="http://rcm.amazon.com/e/cm?t=zx81orguk00&o=1&p=8&l=as1&asins=1565923758&fc1=000000&IS2=1&lt1=_blank&lc1=0000ff&bc1=000000&bg1=ffffff&f=ifr" style="width:120px;height:240px;"></iframe>Steven Feuerstein’s ‘[Oracle PL/SQL Programming](http://www.amazon.com/exec/obidos/ASIN/1565923359/zx81orguk00)‘ book has, over the last couple of years, become my bible on the subject of writing sizable Oracle PL/SQL programs. As I said [in my review](/computing/opinion/plsqlprogramming.html), it’s useful because it covers just about everything, including the things that don’t work.

So if that book covers just about everything, why would anyone want to buy ‘Oracle Builtin Packages’?

**Content**

In fact, as the first chapter of the book explains, this entire book was origianlly chapter 15 of ‘PL/SQL Programming’ but Oracle complicated things by adding more to the PL/SQL programming language (all the pseudo-object oriented stuff in version 8 ) and many more new or enhanced packages. The result: either a single two thousand page monster, or two more reasonably sized tomes.

But like the first book, this is still a bit of a monster in its own right. It stands at 931 pages and there’s very little padding; if only all technical books had such a high signal-to-noise ratio!

It seems rather pointless to go into detail on the content of all the different sections…

The two chapters that I’ve used the most are those on DBMS\_FILE, which allows you to manipulate operating system files, and DBMS\_SQL. Just about everything I know about these modules I learned from this book. When I was originally writing the code, ‘Oracle Builtin Packages’ was by my side, open at the relevant page. When colleagues mistakenly thought I knew what I was talking about, this book was open beneath my desk giving me superiour bluffing ability.

The main critisism that I can think of is that some of the material is getting rather out of date. The DBMS\_SQL package is no longer as necesary as it used to be — Oracle 8i introduced some new syntax to the PL/SQL language that largely replaces it.

**Conclusion**

I’ll be brutal: in marked contrast to Feuerstein’s first book, if you regularly write PL/SQL code you *can* get by without reading this book.

But you will be more productive if you get it. You won’t be spending days writing code to do things that Oracle have kindly supplied a routine to do and you won’t give up on PL/SQL and write a program in Pro\*C because you don’t realise, for example, that you *can* manipulate files.

No, this book is less vital than ‘Oracle PL/SQL Programming’ but it is still a thorough, well organised and useful book. It’ll quickly pay for itself many times over, and that’s a very high recommendation.

**The facts**

Author: Steven Feuerstein, Charles Dye, John Beresniewicz

Cost: US$46.95

ISBN: 1-56592-375-8