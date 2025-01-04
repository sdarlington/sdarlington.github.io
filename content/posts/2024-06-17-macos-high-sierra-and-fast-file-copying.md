---
id: 93912
title: 'macOS High Sierra and fast file copying'
date: '2024-06-17T17:20:00+01:00'
author: 'Stephen Darlington'
excerpt: 'How does the Mac make "lightning fast" file copies?'
layout: post
guid: 'https://www.zx81.org.uk/?p=93912'
permalink: /computing/opinion/macos-high-sierra-and-fast-file-copying.html
categories:
    - Opinion
tags:
    - apple
    - mac
    - technology
---

I’ve seen people claiming that macOS High Sierra and its new file system, APFS, makes [copying files lightning fast](http://www.shirt-pocket.com/forums/showpost.php?p=33846&postcount=9). This is not true. Here’s why.

In short: most of the time spent copying files is the physical copying of bits from one place to another. Unless you can avoid doing that, you’re, at best, going to be a few percent faster.

The longer version relies on the slightly hidden caveat: “unless you can avoid doing that.”

Note the wording on [Apple’s website](https://www.apple.com/macos/high-sierra-preview/):

> **Responsive**. Designed to make common tasks like duplicating a file and finding the size of a folder’s contents happen instantly.

It doesn’t say “copying” is says “*duplicating*.” It’s easy to see where the confusion comes from. In English, the words copying and duplicating roughly mean the same thing. Computers are not so forgiving.

Here is a quick primer in file systems. Actually, super-quick.

Files are made up of two bits. There’s the actual file. That is, your presentation or your report or your spreadsheet. And there’s the metadata, stuff like where it is in the file system, when it was created and its name.

Normally, for every file there’s one chunk of metadata. But the file and the metadata are somewhat independent. If you want to move a document from one folder to another, for example, instead of moving the whole file you can get the same effect just by moving the metadata. It’s quick, no matter how large the file is.

If you want to *copy* the document, you’d take a copy of the file and then create a new chunk of metadata so you can find it again. That’s what the Mac has always done.

ADFS is a bit cleverer. If you *duplicate* a document, it simply creates a new chunk of metadata and points it at the same file. Only when you edit and save a new version does it actually create a complete new copy.

There are two hidden caveats in there. First, if you actually need to make a copy — say you’re copying it to a USB stick — then an actual copy still needs to be made and ADFS is no quicker than before. And second, when you later edit the file, you still have to send the whole document back to disk.

Ultimately, you only really save time if you duplicate files and then never change them! Sadly I can’t think of a use-case for that.

None of which is to say that ADFS is bad. Quite the contrary. It’s a modern file system which in theory is safer and better optimised for the current (and future) generations of hardware than HFS+. It’s a Good Thing but not something that most users should really care about.

*This post was originally shared on Medium in 2017.*