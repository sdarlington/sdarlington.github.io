---
id: 3948
title: 'Learning Swift'
date: '2014-06-12T17:39:20+01:00'
author: 'Stephen Darlington'
excerpt: 'My first attempt at writing a program in Swift proves problematic.'
layout: post
guid: 'http://www.zx81.org.uk/?p=3948'
aliases: ['/computing/programming/learning-swift.html']
categories:
    - Programming
tags:
    - apple
    - ios
    - language
    - mac
    - Programming
    - swift
---

[Swift](https://developer.apple.com/swift/) is a new programming language designed by Apple for development on OS X and iOS. I thought that I should try to learn it a little so I decided to convert a non-trivial collection of classes from one of my apps ([www.cut](http://www.wandlesoftware.com/products/www-cut)) into Swift. I always find it better to work on a real project rather than just to play around with things aimlessly. Also, by re-working an old project, I knew that all the problems I would find would be language related rather than anything to do with the architecture.

The classes are also data related rather than being UI, so it is mostly a test of the language itself rather than how it interfaces with Objective C.

First impressions are good. Swift is mostly nice and consistent, which although sounding like damning with faint praise, is actually a compliment. I read a little of the language guide and dove straight in. A lot of the attempts to get the following right were me just typing stuff, guessing the syntax rather than looking it up.

Quite by accident I think my code sample inadvertently shows an area of strength for Objective-C and weakness for Swift.

The idea of the code is that it reads a Plist, instantiates a class based on that configuration and fills in a number of properties.

The first half of the code looks like this:

```
        NSError* error = nil;
        NSString *plistPath = [[NSBundle mainBundle] pathForResource:@"XXX" ofType:@"plist"];
        NSData *plistXML = [[NSFileManager defaultManager] contentsAtPath:plistPath];
        NSDictionary *temp = (NSDictionary *)[NSPropertyListSerialization propertyListWithData:plistXML
                                                                                       options:NSPropertyListMutableContainersAndLeaves
                                                                                        format:NULL
                                                                                         error:&error];
        NSArray* values = [temp objectForKey:@"Entries"];

```

This was pretty straight forward to convert into Swift, though the type system gave me issues:

```
    let plistPath =  NSBundle.mainBundle().pathForResource("XXX", ofType: "plist")
    let plistXML = NSFileManager.defaultManager().contentsAtPath(plistPath)

    var error:NSError? = nil
    var format:CMutablePointer<NSPropertyListFormat>? = nil
    let immutable:NSPropertyListReadOptions = 0
    var pList = NSPropertyListSerialization.propertyListWithData(plistXML,
        options:NSPropertyListReadOptions(NSPropertyListMutabilityOptions.Immutable.toRaw()),
        format:format!,
        error: &error) as NSDictionary

```

Getting the options property seems very clumsy; I’m sure that there must be a better way of doing it.

I had a real problem with the in/out parameters `format` and `error`. Not only was the documentation confusing but the Swift Playground kept crashing making it difficult to distinguish between what *I* was doing wrong and where the compiler itself was messing up. It’s also a bit odd that, though both are in/out parameters, that they both need different methods to extract the values.

(To be fair, this is a beta and it is the first version of a whole language and compiler. I mention the crashes not because they’re unexpected or even especially bad, just as an honest description of the difficulty I had.)

The next section, *using* the data in the plist, was much more problematic. The code looks like this, but I’ve trimmed a lot so what we have here isn’t terribly useful now!

```
        proxy = nil;
        for (NSDictionary* i in values) {
            if ([thing isEqualToString:[i objectForKey:@"Class"]]) {
                dynamicClass = NSClassFromString([i objectForKey:@"BaseClass"]);
                proxy = [[dynamicClass alloc] init];
            }
        }

```

I didn’t do the straight conversion. A few more years of Cocoa programming allowed me to notice an optimisation:

```
    let valueList = values.filteredArrayUsingPredicate(NSPredicate(format: "Class = %@", value))
    let valueData = valueList[0] as NSDictionary

```

This same approach would work in Objective-C.

Next I tried:

```
  let dynamicClass = NSClassFromString(valueData["BaseClass"])
  let proxy = dynamicClass()

```

The first line works as expected. The second line doesn’t compile.

Is there anything else that we can do with `dynamicClass`? Let’s see. It’s an `AnyClass` which is a type alias for `AnyObject.Type`. Which doesn’t really help.

I tried casting it to a base class but no matter what I tried I couldn’t alloc/init it (in Objective C terms).

Josh Smith figured out how to do it by [creating a factory class in Objective-C](http://ijoshsmith.com/2014/06/05/instantiating-classes-by-name-in-swift/).

I tried (and failed) to get it to work by calling some of the Objective-C runtime directly:

```
var bytes:Byte[] = [0,0,0,0]
let b = objc_constructInstance(a, &bytes)

```

But the second line doesn’t work when using ARC. (To be fair, Xcode struck through the definition so I didn’t have much confidence that it would work!)

So that leaves Josh’s call out to Objective-C to be the best method that I’m aware of.

In the end I just used a `switch` statement to select between the relatively limited number of options that I had to choose between. Not as clever, but maybe that’s a good thing?