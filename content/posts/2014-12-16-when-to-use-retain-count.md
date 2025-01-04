---
title: When to use -retainCount?
date: '2014-12-16T17:11:54+00:00'
author: 'Stephen Darlington'
excerpt: 'In the pre-Swift days, the answer to a common question was "No"'
layout: post
categories:
    - Computing
tags:
    - objectivec
    - programming
    - mac
    - ios
    - apple
---

Preamble: _In pre-Swift and pre-ARC days of development on Apple's platforms, it was necessary to "manually" retain
and release objects as you used and discarded them. One common, but incorrect, pattern that kept
reappearing was the idea that you could use the retainCount method to ascertain whether an object
was still being used._

# When to use -retainCount? Never!
        
There's pretty much never a good reason to use <code>-retainCount</code>. Here's a short and mildly abusive explanation why.

## What about when I need to <em>x</em>?

No.

## But so-and-so said it was a good idea in this case?

Still no.

## I used it in some code already and it worked fine!

Did it, by any chance, look like this?
          <p>
<pre>while ([a retainCount] > 0) {
  [a release];
}</pre></p>
          
Good luck with that. Please let me know which app so I can avoid buying it.

## But it works! It really does!

Perhaps. But probably for the wrong reasons. And it won’t take much to break it.
          
## Are you going to give flippant answers to all my questions?

If you’re going to keep using <code>-retainCount</code> after the advice of lots of knowledgeable and influential people, including the people who wrote the framework, I reserve the right to.

## I’ve enabled ARC and it won’t let me use <code>-retainCount</code> any more.

See the above comment about Apple recommending against using <code>-retainCount</code>.

## Okay, okay. I get the idea, but why?

Basically it doesn’t say what you think it does. Or rather, it does but it’s never accurate in any non-trivial case.
 
For example:
 
* You'd think that <code>[NSNumber numberWithInt:1]</code> would have a retain count of 1. It doesn't. It's 2.
* You'd think that <code>@"Foo"</code> would have a retain count of 1. It doesn't. It's 1152921504606846975.
* You'd think that <code>[NSString stringWithString:@"Foo"]</code> would have a retain count of 1. It doesn't. Again, it's 1152921504606846975.
 
<p>(<a href="http://stackoverflow.com/a/4636477/2998">H/T to Dave DeLong for these.</a>)</p>

## That’s just in Apple’s code. I want to use it in code I’ve written.

Still no.

Did you ever use autorelease? The value of retainCount includes only the current retain count. You have no idea whether it has been autoreleased. If you add a release now it might release again when the autorelease pool drains.

## So how do I know whether I should release or not?

If you use ARC, the simple answer is that you don't. (Unless you use Foundation classes, in which case read on.)

You need to understand your code.
 
It’s pretty straightforward. If you alloc, copy, new or retain an object you need to release it. Otherwise you don’t.
 
## I’m still not convinced.

As I say, let me know which app you’re using so I can not buy it.
 
But first, have a look at the following resources. Hopefully they’ll change your mind.
 
* <a href="http://www.friday.com/bbum/2011/12/18/retaincount-is-useless/">retainCount is useless </a>
* These Stack Overflow questions: <a href="http://stackoverflow.com/questions/3730804/how-many-times-do-i-release-an-allocated-or-retained-object/3730835#3730835">1</a>, <a href="http://stackoverflow.com/questions/4636146/when-to-use-retaincount">2</a>


