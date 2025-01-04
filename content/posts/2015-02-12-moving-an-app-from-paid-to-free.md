---
id: 4209
title: 'Moving an app from Paid to Free'
date: '2015-02-12T16:58:12+00:00'
author: 'Stephen Darlington'
excerpt: 'Too many people say that it''s not possible to migrate a paid iOS app to a free one supported with in-app purchases. Here I explain how to do it.'
layout: post
guid: 'http://www.zx81.org.uk/?p=4209'
aliases: ['/computing/programming/moving-an-app-from-paid-to-free.html']
enclosure:
    - "http://devstreaming.apple.com/videos/wwdc/2013/308xex4x6ybggtlw4ztv0sg5btp/308/308-HD.mov?dl=1\r\n2677472578\r\nvideo/quicktime\r\n"
categories:
    - Programming
tags:
    - developer
    - ios
    - ipad
    - iphone
    - security
---

I’ve seen quite a [few](http://stackoverflow.com/a/28392177/2998) [people](http://stackoverflow.com/a/9494971/2998) saying that it isn’t possible to move an iOS app from paid to being free with an in-app purchase to unlock the full functionality. Fortunately they’re wrong.

“Traditionally” I would have had to remove version one from sale and offer a completely new app, which would have meant that existing users would have to pay again to get the same functionality. Or I’d have to support two apps. Or I’d keep the same app in the store and all existing users would get downgraded to the free version. None of these solutions seemed fair to existing users.

What I wanted was for people who had bought version one to get the full, unlocked version and for new users to be promoted for the paid upgrade.

Since iOS 7 came out in 2013 that it entirely possible. I’ll explain how it’s done here. This isn’t just some theoretical “I’ve seen the documentation” claim – I’ve done it with one of my own apps, [Rootn Tootn](http://www.wandlesoftware.com/products/rootntootn).

The really short answer: take a look at the [session 308 video from WWDC 2013](http://devstreaming.apple.com/videos/wwdc/2013/308xex4x6ybggtlw4ztv0sg5btp/308/308-HD.mov?dl=1). That’s the only information from Apple that explains how to do it. They *have* documented the API calls that are required but the actual process is left as an exercise for the interested student. And there are quite a few steps if you want to do it properly.

Firstly you need to get the app receipt. Before iOS 7 this only made sense for IAP but now they are available for all purchases and come in the same format as receipts from the Mac App Store.

Receipts have a number of useful features. In the past they have been used to validate purchase, and they can still be used for this. What’s interesting with the new receipts is that they include both the original purchase and the version number of that original purchase. This means that we can decide whether a user gets the paid functionally by looking for either an in app purchase *or* a purchase date before a particular time or, more likely, before a particular version.

When you download an app you should get a receipt automatically but you can also use the `SKReceiptRefreshRequest` class to force one to be generated. (This is also useful during development where, obviously, there is no receipt.)

Once the refresh has completed, you use `[NSBundle appStoreReceiptURL:]` to access the receipt.

Once you have the receipt the bad news starts.

It’s not in a user friendly format. And Apple do not provide any APIs to read it. Check out [Apple’s documentation](https://developer.apple.com/library/mac/releasenotes/General/ValidateAppStoreReceipt/Chapters/ValidateLocally.html):

> The outermost portion (labeled Receipt in the figure) is a PKCS #7 container, as defined by RFC 2315, with its payload encoded using ASN.1 (Abstract Syntax Notation One), as defined by ITU-T X.690. The payload is composed of a set of receipt attributes. Each receipt attribute contains a type, a version, and a value.

If security is important to you, you should probably write your own code to do this. ASN.1 is a standard format and it’s not *that* hard.

There are apps that generate the validation code, such as [Tighten Pro](https://itunes.apple.com/gb/app/tighten-pro-app-security-code/id427083596?mt=12&at=11lmMT&ct=zx81) and [Receigen](https://itunes.apple.com/gb/app/receigen/id452840086?mt=12&at=11lmMT&ct=zx81). I can’t vouch for either of them but the reviews seems positive.

There are also Open Source projects that do the same thing. I’ve used [RMStore](https://github.com/robotmedia/RMStore); there’s also [VerifyStoreReceiptiOS](https://github.com/rmaddy/VerifyStoreReceiptiOS). The main disadvantage of these is that, as standard, open code it makes it easier for crackers to reverse engineer how you remember that a purchase has been made.

And there you have it. It *is* possible. It’s just a lot harder than you might imagine. Remember this when someone tells you that it can’t be done.