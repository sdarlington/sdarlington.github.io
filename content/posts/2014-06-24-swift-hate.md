---
id: 3969
title: 'Swift Hate'
date: '2014-06-24T17:27:05+01:00'
author: 'Stephen Darlington'
excerpt: 'Unless Swift is a big practical joke by Apple it''s not going away any time soon. Get used to it.'
layout: post
guid: 'http://www.zx81.org.uk/?p=3969'
aliases: ['/computing/opinion/swift-hate.html']
categories:
    - Opinion
tags:
    - apple
    - development
    - ios
    - Language
    - mac
    - Programming
    - swift
---

I’m seeing a surprising amount of vitriol aimed at Swift, Apple’s new programming language for iOS and Mac development. I understand that there can be reasoned debate around the features (or lack thereof), syntax and even the necessity of it but there can be little doubt about the outcome: if you want to consider yourself an iOS developer, it’s a language that you will need to learn.

The only variable I can think of is *when* you learn it.

I think it’s perfectly reasonable to delay learning it as you have code to deliver *now* and because Swift is, well, very beta currently.

But asking what the *point* of Swift is not constructive. Asking what problems can be solved exclusively by Swift makes no sense at all <s></s> you can do almost anything in most programming languages. Just because Intercal is Turing complete doesn’t mean that you’d want to use it for any real work. What varies between languages is what’s easy and what’s hard.

Objective-C undoubtedly makes some things easier than Swift. It’s a more dynamic language and its C foundations open up a lot of low-level optimisations that probably are not there in higher level languages.

But that same flexibility comes with a price: segmentation faults and memory leaks; pointers; easy-to-get-wrong switch statement; a lack of bounds checking. It also inherits a lot of ambiguity from original C language specification which makes certain automatic optimisations impossible.

How many applications require low-level optimisations more than safety? (And that’s ignoring that the biggest optimisations are usually found in designing a better algorithm or architecture.) How often is it better to have five lines of code instead of one? Every line is a liability, something that can go wrong, something that needs to be understood, tested and maintained.

Whatever its failings, it’s already clear that Swift is more concise and safer than Objective C.

There are absolutely applications where Objective C, C or C++ would be a better choice than Swift. It’s the old 80-20 rule applied to a programming language. And, for those resistant to learning a new language, the 80% is not on “your” side.

Right now, some of this requires a bit of a leap of faith. Swift clearly isn’t finished. You can either learn it now and potentially have some say on what the “final” version looks like, or you can learn it afterwards and just have to accept what’s there. But, either way, you’ll probably using it next year. Get used to it.