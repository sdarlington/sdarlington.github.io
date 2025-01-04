---
id: 3863
title: 'CameraGPS debrief'
date: '2014-02-04T18:34:57+00:00'
author: 'Stephen Darlington'
excerpt: 'No software ends up exactly as you envisage at the beginning. My new app, CameraGPS, is no exception.'
layout: post
guid: 'http://www.zx81.org.uk/?p=3863'
aliases: ['/computing/opinion/cameragps-debrief.html']
categories:
    - Opinion
tags:
    - development
    - dropbox
    - ios
    - ipad
    - iphone
    - mac
    - Software
---

As happy as I am with the way that my new app, [CameraGPS](http://www.wandlesoftware.com/products/cameragps), a GPS logger application for people who want to geotag their photographs, came out I can’t say that it’s exactly as I envisioned it at the start of the process.

The idea was something like this: many of the GPS logger apps in the App Store require you to either use iTunes file sharing (who connects their iPhone’s to iTunes any more?) or mail yourself the exported document or sign up to some third party fitness or trekking website. Mailing yourself stuff just didn’t feel very slick and I didn’t want to record my trails for fitness purposes.

I felt that there must be a better way. The better way, I thought, was to use iCloud to share the files between iOS and a Mac. This would require writing a recorder app for iPhone and an “exporter” app for the Mac.

It didn’t work out that way in the end. Here’s why.

You see all kinds of horror stories from people who have had to deal with iCloud. Most of those stories come from people who used the Core Data syncing, while there are a few apps that successfully use the document syncing model, not least some of Apple’s own. Using the document storage I figured that, worst case, if something gets screwed up it would only affect a single trail. Using Core Data syncing, an error could mean corrupting the whole database.

So this became the plan: record each GPS trail into a separate document. Because I wanted to “random access” parts of each trail and because I didn’t want to have to load the whole trail into memory all the time, I decided to use Core Data to manage the document. On iOS this is called UIManagedDocument.

The first and most obvious [fail](https://twitter.com/search?q=%23fail&src=typd "ing... ") here is with [UIManagedDocument’s](https://developer.apple.com/library/ios/documentation/uikit/reference/UIManagedDocument_Class/Reference/Reference.html "ent for") cross platform capabilities. Or rather the lack of them. Unless you count iPhone to iPad as cross platform it just doesn’t work. There is a class on the Mac called [NSPersistentDocument](https://developer.apple.com/library/mac/documentation/cocoa/reference/ApplicationKit/Classes/NSPersistentDocument_Class/Reference/Reference.html "package") that is also a Core Data store and looks on the surface to do exactly the same thing… but it’s in a different format. On iOS it’s a “package” which includes a Core Data store. On the Mac it’s *just* the store. [Mike Abdullah](https://github.com/karelia/BSManagedDocument) has written an open source component that attempts to be bridge the gap but — as we’ll see shorty — I didn’t get to the point where I was able to test it in anger.

But let’s take a step backwards. Let’s assume that all we need is to move data between iPhone and iPad. Then what?

Well, *technically* it works — in the sense that documents transfer between machines — just not in a way that would make sense to ship.

To make sense of why it doesn’t work let’s take a quick diversion to look at the format of a UIManagedDocument. As hinted above, it’s not a file. Rather it’s a “package” which a number of files within.

An important file is called DocumentMetadata.plist. This tells you about the rest of the package and is created when the document is. There’s little in here that needs to be changed after document creation. The interesting stuff is all stored in a SQLite file, which is stored in a folder.

When files are stored in iCloud you can’t just use NSFileManager to poke around and see what’s there. Instead you create a query using NSMetadataQuery — which supports both a predicate and a sort descriptor — and listen for updates. Updates come in two parts, the initial state and then changes to that state.

After a few false starts I ended up using KVO to populate a table view showing the current list of documents. This worked nicely, showing the full list, updating automatically when changes arrived over the network.

But, and it’s a big but, what if you want to sort the list. Pretty basic requirement, no?

One of the fun things about NSMetadataQuery is that it can only look for files. Folders are “invisible.”

Most of [Apple’s documentation](https://developer.apple.com/library/IOs/releasenotes/DataManagement/RN-iCloudCoreData/) — where there is any — suggests searching for the DocumentMetadata.plist. Which makes sense but with two significant drawbacks: every file that you’re looking for now has exactly the same name; and the modification date is the *creation* date of the document rather than the time of the last update.

This means that you can’t sort the documents alphabetically or by modification date using only the metadata predicate. To get the names you need to listen for updates, copy them elsewhere and then butcher the file name, that is removing the last component and possibly the file extension.

To get the last modification date you probably need to open the document and do a Core Data query. This sounds pretty straight-forward but, again, there are difficulties. Remember that NSMetadataQuery tells us what’s available in iCloud rather than what has been downloaded onto the current device. Just because the query tells us the file is in iCloud doesn’t mean that you can open it immediately.

UIDocument helps us a bit here: if you ask to open a document it will download it if necessary. However there’s a big difference between opening a local file and downloading one over the network and *then* opening it. Also remember, at this point we’re not opening it as the result of a user request. We’re just trying to find the last modification date so that we can sort the list of documents conveniently.

None of this, of course, is impossible. It’s just a lot of faff for something that pretty much every app that wants to use UIDocument must have to go through.

Okay, so we get all that done. We’re good to go now, right? Not quite.

Part of the idea of using a UIDocument was that it would appear as a, well, document. But that whole thing about what NSMetatadataQuery “sees” comes back to haunt us.

The short, weird version is that if you configure the application to look for DocumentMetadata.plist, then that’s what is seen in the Settings app. Not very helpful as *all* the documents will all have the same name.

On the other hand you can configure the app to “know” about the document type. This means that the Settings app understands that they’re document and displays them with the correct “file” name. Unfortunately then the *app* can’t see the documents properly. Specifically, you can search for the document by name — which is nice — but you can’t actually open it. It’s odd and I’m not entirely sure what goes wrong, but when you call openWithCompletionHandler: it never actually calls the completion handler and the document never becomes available for use. (I initially thought that I just wasn’t being patient enough. I later accidentally left the app running for over two hours and the completion handler still never ran. That convinced me that it wasn’t a patience thing.)

I convinced myself that this couldn’t possibly be how it was supposed to work. [My question on Stack Overflow](http://stackoverflow.com/questions/19841753/uimanageddocument-icloud-and-document-types " said that") didn’t get any answers and a reply to [another, similar question](http://stackoverflow.com/questions/9026242/nsmetadataquery-ignoring-custom-file-package-type "by design.") said that the behaviour was “by design.”

I think it’s just broken and that no one is really using it. Either that or there’s a secret handshake that you have to give to the right person at WWDC.

So what’s shipping? Pretty much none of the above. I read about the new iOS 7 methods of Core Data – iCloud syncing and liked what I saw. Additionally iOS 7 comes with a few more APIs with better error handling hooks. This made me happier shipping with Core Data syncing. Just using “raw” Core Data meant that I could simplify a lot of code, use NSFetchedResultController and remove a bunch of the more fragile iCloud code (mostly NSMetadataQuery). While I was quite pleased with the KVO code I wrote, having far less code overall is a much bigger win.

And, in case you were wondering, I also de-scoped the Mac app and integrated Dropbox support instead.

But the bottom line is that this is all a lot harder than it should be. My concerns originally were around error conditions — something that has been very weak in iCloud since it’s introduction in iOS 5 — but it quickly morphed into questions about how it’s all supposed to work at all.

I once quipped on Twitter that you can tell which APIs are the ones Apple uses themselves as they’re the well designed ones. I think it’s pretty clear that Apple don’t use UIManagedDocument.