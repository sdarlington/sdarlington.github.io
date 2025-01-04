---
id: 3977
title: 'Swift Types'
date: '2014-06-30T16:01:54+01:00'
author: 'Stephen Darlington'
excerpt: 'Is it good to start a new programming language with a lot of cruft pre-installed?'
layout: post
guid: 'http://www.zx81.org.uk/?p=3977'
permalink: /computing/programming/swift-types.html
categories:
    - Programming
tags:
    - apple
    - ios
    - Languages
    - mac
    - Programming
    - swift
---

If you look at the Swift Language guide, you get the distinct impression that the type system is sleek and modern. However the more you dig into it the more eccentricities you find.

The one I’m going to look at today makes sense only if you look at the problem domain from a slightly skewed perspective. I’ve been trying to think whether this is a sensible, pragmatic way of designing a language or a mistake. Judge for yourself.

So, the feature. Let’s define a dictionary:

```
var test1 = [ "Foo" : "Bar" ]

```

Check the type and we find that it’s of type `Dictionary<String,String>`. The generics and type inference are doing exactly what you’d image.

```
test1["Test"] = "Works"

```

So basically [it’s all good](http://www.bbc.co.uk/programmes/b00yw1t9).

So, what type is this expression?

```
var test2 = [:]

```

And why does this not work?

```
test2["Test"] = "Doesn't work"

```

Let’s take a step back. What’s the problem? Well, `[:]` is an empty dictionary but give us no clue what the type is. Remember, Swift dictionaries and arrays use generics, so the compiler only allows objects of a particular type to be added.

A [good guess](https://twitter.com/pilky/status/483571292072050688 "bject</c") for the type would be `Dictionary<AnyObject,AnyObject>`. But a little fishing around tells you that’s not the case because `AnyObject` is neither “Hashable” or “Equatable” and keys need to be both.

The answer? `test2` is an `NSDictionary`. That is, in this one circumstance, Swift extends outside its native dictionary type and decides to use a class found in Foundation.

Once you know that, it is clear that the second line should be:

```
test2.setValue("Does work now", forKey:"Test")

```

Maybe if you’re familiar with the guts of both Objective C and Swift this behaviour makes sense, but a language built-in returning a completely different type just because it can’t figure out the type feels broken to me.

In the end I think I’ve convinced myself that, while it might be convenient to allow this syntax, it’s a bad idea to saddle the language with these semantics so early on. In a few years when no one uses Objective C or when Swift is no longer fully tied to Cocoa, will this make sense?

I would prefer to see it being a compiler error with the correct approach being explicit with the type:

```
var test2:Dictionary<String,String> = [:]

```

Thoughts?