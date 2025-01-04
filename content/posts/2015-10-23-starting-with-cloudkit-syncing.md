---
id: 4333
title: 'Starting with CloudKit Syncing'
date: '2015-10-23T11:51:37+01:00'
author: 'Stephen Darlington'
excerpt: 'Got that syncing feeling when trying to use CloudKit?'
layout: post
guid: 'http://www.zx81.org.uk/?p=4333'
permalink: /computing/programming/starting-with-cloudkit-syncing.html
categories:
    - Programming
---

One of the slightly more hidden features of [CloudKit](https://developer.apple.com/icloud/), Apple’s cloud-based back-end service for applications, is that you can use it to synchronise content as well as simply query it. I use this approach to sync favourite search terms between devices in my app [Yummy](http://www.wandlesoftware.com/products/yummy).

However, I found the process wasn’t as well documented as it might be. It’s all there, but it’s written as many *man* pages are: it makes total sense *if you already know what you’re looking for*. This post is my attempt to make the process clearer.

We’ll start by inserting some data into the cloud data store and then try to get it back out again.

Pushing data to CloudKit is pretty straight forward. As we’ll see later there’s a little more preparation required in practice, but at it’s simplest it looks like this:

```
// Get a reference to the private cloud database
CKDatabase* db = [[CKContainer defaultContainer] privateCloudDatabase];

// create a new record
CKRecord* myRecord = [[CKRecord alloc] initWithRecordType:@“Record” zoneID:zoneID];

// set the interesting values
[myRecord setObject:@“Data” forKey:@“Key”];

[db saveRecord:myRecord completionHandler:^(CKRecord* record, NSError* error) {
  // error handling
  // save a local copy in cache
}];

```

We’ll come back to the zoneID variable used in the second line.

It’s asynchronous and only takes a couple of API calls. Nice.

Once data has been pushed to the cloud you have to get it back again. In my case there are few enough records that I *could* just download everything and do a local “diff.” That would look like this:

```
// create a query
CKQuery* query = [[CKQuery alloc] initWithRecordType:@“record”
                                              predicate:[NSPredicate predicateWithValue:YES]];

// define what to do with the records to be returned
CKQueryOperation* queryOperation = [[CKQueryOperation alloc] initWithQuery:query];
queryOperation.recordFetchedBlock = ^(CKRecord* record) {
  // do something with each record
};

// fire off the query
[db addOperation:queryOperation];

```

Doing the local diff is left as an exercise for the reader.

Again, just a few lines of code. (Quick aside: I’m not sure if it’s a good thing that the block is called for every record individually. It feels like it might be easier given a block of records, but CloudKit is generally consistent about this one record at a time approach.)

But that feels like it’s missing the point. CloudKit supports just getting a list of what’s changed since the last sync.

The class to find the records that have changed since the last sync is `CKFetchRecordChangesOperation`, but if we put that in a method:

```
CKFetchRecordChangesOperation* changesOperation = [[CKFetchRecordChangesOperation alloc] initWithRecordZoneID:[CKZoneID defaultZone]

```previousServerChangeToken:nil];

```
[[[CKContainer defaultContainer] privateCloudDatabase] addOperation:changesOperation];

```

(The `nil` token means we’re starting from scratch — get us everything. Next time we sync, we pass in the token given at the end of the *last* sync.)

However if we run it we get an error:

```
<CKError 0x7fd326282bb0: “Server Rejected Request” (15/2027); server message = “AppDefaultZone does not support sync semantics”; uuid = 00138311-1714-4651-BE36-9D85B3CB5D51; container ID = “containerID”>

```

So, in short, the *default* configuration does not allow us to sync! We have to create a new record zone to store our records. A corollary of this is that you can only sync *private* stores, since you cannot create new zones for the public cloud database.

In principle this is quite simple but in practice it can get a little hairy as every call to CloudKit is asynchronous and there’s lots of error handling to consider.

I’m not going to show all my working (because what I have is pretty hacky and I’m sure you can do better) but the algorithm is:

1. Are we logged into iCloud? If not, give up now
2. Do we have a record of the current zone ID? If so, jump to step 7
3. Fetch the list of zones that we can use
4. Loop through the list returned. If there’s one we recognise, save the reference and jump to step 7
5. Create a new zone
6. Save the Zone ID in the completion handler
7. Now get on with our sync / insert / update / delete operation

Note that queries tend to pick the right zone automatically, so if you’re searching rather than syncing you don’t need to worry about this.

And that’s it. Syncing *is* possible, just a little convoluted.