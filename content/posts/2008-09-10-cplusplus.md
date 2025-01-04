---
id: 63
title: C++
date: '2008-09-10T06:23:13+01:00'
author: 'Stephen Darlington'
excerpt: 'I continue my (very irregular) series of articles discussing various programming languages. This time it''s the turn of C++.'
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/programming/languages/c-2.html'
permalink: /computing/programming/languages/cplusplus.html
categories:
    - Languages
tags:
    - Computing
    - development
    - Languages
    - Opinion
    - Programming
---

**Introduction**

I don’t want to start off on the wrong foot again, but I’m afraid I might have to. If you read my discussion of the [C programming language](/computing/programming/languages/c.html) you may imagine that I’d like C++. After all, C++ fixes some of C’s idiosyncrasies, adds object orientation and a whole host of new features.

You’d be wrong though. In many ways I consider C++ to be a step backwards from its parent and this piece will hopefully explain why.

**The big things in life**

Identifying the main thing wrong with C++ is easy when you start making a list of features. I don’t mean a list trying to identify things it does badly, but a genuine feature list, stuff like object orientation, exceptions, strong-ish typing, multiple inheritance… Well I’ve only just started, but there’s a huge list.

And that is the problem. C++ has tried to incorporate just about every interesting software engineering development that has been made over the last twenty-five years. In some ways that’s a very good thing: it allows programmers to build code in the most appropriate way which ever that way might be.

The problem is that there’s more than one way to skin any particular cat. While just about any approach is fine on a small program, one with a single developer, when you have a team writing code if there’s no consistency in approach you get the situation where no-one is able to understand the whole. There is no one head big enough.

While There’s More Than One Way To Do It is a great motto for [Perl](/computing/programming/languages/perl.html), as a language it has a very different objective. Most Perl programs are ‘hacks,’ small programs designed to solve a particular problem. C++ is a hard-core software engineering language; large teams of developers are common. The same approach used for small programs just doesn’t work for bigger systems. I can build a thousand line program at the keyboard, but a ten million line system? Anyone that thinks they can are deluding themselves. Even on the off-chance that they aren’t, other people need to understand it too. No-one is ever around for ever and no-one is indispensable (except in the case of bad management, but that’s a different story).

**Counter Arguments**

People often cite C++’s similarity to C as a major plus. If you’ve already learned C, then C++ is easy, right? Just a few extra commands, use “class” instead of “struct” and you’re well away. Except some of the worst C++ code I’ve ever seen has come from people who think like that. Using “//” to start your comments rather than “/\*” doesn’t make you a C++ programmer!

There are, however, some benefits for C programmers using C++ compilers. They tend to be less forgiving of bad code, they often give better diagnostics and error messages. But so do Java and C#, only more so. And the jump from C to Java is probably easier than moving from C to C++.

**Conclusion**

If we think right back to to the beginning of the development of programming languages, we remember that they were designed to simplify things; they were designed so that you could think about the problem rather than what the machine would do.

For the audience that they were aimed at, many of the earlier languages did just that. Fortran allowed scientists to write programs (in fact it’s still being used). Cobol put a greater focus on the business than had ever been the case.

And this is where C++ falls down. Its audience is software engineers, people who write very large and complex applications. Yet its complexity actually hinders development. With a large team, “write-only” code, programs that no-one can understand once they have been constructed, become not just possible but almost guaranteed. There are so many ways of doing the same thing, so many ways to shoot yourself in the foot, that the odds of it being both bug-free and maintainable are almost zero.

C++ does have its plus points, though. It is an excellent language to show how smart you are. If you can understand the entire language and write huge, complex and error-free programs in your sleep, you are clearly much more clever than I am.

Myself, I prefer to fight the problem rather than the development language.