---
id: 62
title: C
date: '2001-03-25T13:25:10+01:00'
author: 'Stephen Darlington'
excerpt: 'C is one of the most popular and well used programming languages on microcomputers. Here we wrestle with some of its features. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/programming/languages/c.html'
aliases: ['/computing/programming/languages/c.html']
categories:
    - Languages
tags:
    - Computing
    - Language
    - Opinion
    - Programming
    - unix
---

**Introduction**

Talking about C is not easy. Almost all professional programmers have used it at some point and many have a strong attachment to it. I don’t want to start by saying that it’s a poor language, alienating much of my audience, but I figure I’m going to end up doing that anyway so I may as well get it out of the way at the beginning.

Compared to many languages that have come since, and even some that came before, C just isn’t a very good language.

There, I’ve said it.

**History**

 Perhaps more than almost any other language since, C has a rich and famous history. It’s almost impossible to discuss it without also talking a little about the history of Unix.

In 1969, Ken Thompson finally got hold of a PDP-7 and decided to write an operating system for it. (It happened more often than you’d think back then.) That operating system was Unix.

A few years later, Dennis Ritchie designed and built a language based on B (itself based on a language called BCPL) and, creatively, called it C. Unlike its immediate ancestors, C had types and a number of other useful bits and pieces.

C was so useful that Unix was quickly rewritten in it. These days that sounds obvious, but until that point operating systems had always been written in assembler or machine code. This is an important part of computer history.

**Utility**

C became popular largely because it filled a very useful niche. At one extreme you have all the ‘real’ languages. At the time, real computer scientists would have used Algol68. Structured and clever, Algol was a great language but you couldn’t do anything very low level with it.

At the other extreme there is assembler which people had to resort to if they wanted to do anything close to the hardware. Assembler is only one step removed from machine code which makes writing reliable, bug-free code very difficult, especially when you’re building something as large and complex as an operating system.

C fits in the middle. Described by some as a high-level assembler, it allows you to do low level coding, accessing particular memory addresses and the like, *and* use high-level constructs such as functions and types.

<div id="quote">The following books and papers helped me learn to hate C.

“[Practical C Programming](http://www.amazon.com/exec/obidos/ASIN/1565923065/zx81orguk00)” by Steve Oualline.

“[Writing Solid Code](http://www.amazon.com/exec/obidos/ASIN/1556155514/zx81orguk00)” by Steve Maguire.

“[Code Complete](http://www.amazon.com/exec/obidos/ASIN/1565923065/zx81orguk00)” by Steve McConnell.

[Hello world](http://www.cuillin.demon.co.uk/nazz/trivia/hw/hw_c.html). How many nasty ways can you write “Hello World” in C?

</div>**Pointers**

Key to C’s ability to mix high- and low-level constructs are pointers. Most ‘serious’ languages have some concept of a them. Some call them references, some call them links, but they all, basically, refer to something that identifies a chunk of memory. Most other languages only use them when you have to, but they *are* C. No pointers, no language.

You want an array? That’s really a pointer. Pass by reference? A pointer. Strings? Ah, they’re arrays! (Which are pointers.)

The advantages of using pointers for just about everything in the entire language are mainly one sided: it makes writing compilers easier. For the poor souls that actually end up using the language all is not so rosy. As Steve McConnell puts it, “pointers are one of the most error-prone areas of modern programming” ([Code Complete](http://www.amazon.com/exec/obidos/ASIN/1556154844/zx81orguk00), section 11.9).

Some of the side-effects of using pointers are not immediately apparent, either. In most languages, arrays have bound-checking (the ability for the language to raise an error if you try to access an element that doesn’t exist). But C doesn’t really have arrays, it has pointers and a little syntactic sugar that makes it look like it has arrays. Pointers don’t know how much memory is being pointed to so you don’t get bound-checking. If you’re lucky your program causes a segmentation fault, if not you might corrupt other data or, on some operating systems, your program.

**It takes all types**

Another one of C’s biggest problem is it’s typing. As most people will already know, C allows you to put numbers into character variables, integers into floating points and any number of other nasty combinations. To C they’re all valid, but what they do are not always well defined or consistent. Even the same compiler sometimes does different things depending on the level of optimisation in use, the phase of the moon, etc.

The odd thing is that a weakly typed language doesn’t allow you to do more than one with strong types, it merely allows you to do the wrong thing more easily. For a language used for large-scale software engineering projects the risk of poor code is just too great and weak typing should be outlawed.

I’m sure that people are going to mention the myriad of warnings that modern compilers are able to produce, or that ‘lint’ has been available for nearly as long as the language has been. My counter-argument: I don’t see why you should have to add extra tools or read through pages of warnings in order to correct deficiencies in the source language!

**The good bits**

If C was truly as appalling as I’ve made out so far, no-one would actually be using it. The main ‘win’ for C, as far as I can see, is that it is small, well defined and widely available.

All three merits are in many ways different sides of the same coin (if you can imagine a three sided coin). To make the language well defined, it helps if it’s small. If lots of people are to use it, it needs to be simple enough that they aren’t put off (Ada anyone? Thought not.). Small and well-defined make it easier to write compilers too, meaning that it’s available on everything from the lowliest PC right up to mainframes.

The theory also goes that your programs should recompile on this range of machines too, but that’s not as true as we’d all like to think. If it was true, we wouldn’t need Java or hundreds of ‘#ifdefs’ throughout. My code tends not to be that low-level, but I wouldn’t like to make any promises about its portability. However, that doesn’t make C’s wide availability useless. Even if your program isn’t cross-platform, the skills required are. A C programmer can quickly write code for just about any machine.

**Summary**

I’ve probably written more lines of C code than just about any other language, so when I say that I don’t like it I hope that you can see that I’m not being narrow-minded or prejudiced.

As I’ve mentioned above there are some things that I like about C, it’s just that there is so much to hate about it and, even at the time it was written, there wasn’t an excuse for it!

The languages main features are its weak typing and over-use of pointers, both of which allow developers to make truly horrendous coding errors with ease.

If those were C’s only problems I might be able to forgive it, but they aren’t. C has more ways for both experienced and novice programmers alike to hang themselves than any other language I can think of (with the possible exception of [Intercal](http://catb.org/~esr/intercal/stross.html)). Even if it didn’t have the ‘=’ and ‘==’ operators to confuse, there’s still the wonderful ‘?:’ and a whole host of spectacularly error prone API calls (does *all* your code check the value that ‘malloc’ returns?)

No, C, as a language, is a dinosaur. It deserves to whither and die. If you write anything other than an operating system kernel and use C, switch to another language. You’ll be far more productive when you start battling the problem rather than the language.