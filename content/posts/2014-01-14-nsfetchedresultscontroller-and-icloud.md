---
id: 3813
title: 'NSFetchedResultsController and iCloud'
date: '2014-01-14T17:35:45+00:00'
author: 'Stephen Darlington'
excerpt: 'Things that are supposed to "Just Work" often don''t. '
layout: post
guid: 'http://www.zx81.org.uk/?p=3813'
aliases: ['/computing/programming/nsfetchedresultscontroller-and-icloud.html']
categories:
    - Programming
tags:
    - database
    - development
    - ios
    - ipad
    - iphone
    - objectivec
    - Programming
---

This took me a while to figure out so I thought it was worth blogging about. The short version: I’m using Core Data with iCloud syncing and it works… mostly. When starting up for the first time — <s></s>when there is already data in iCloud — <s></s> none of the data appears in a table view, but restarting the app correctly displays it.

I know what you’re thinking: you’re not merging the updates into the right managed object context. Nope. Sorry. Thinking that was the problem is probably why it took me quite so long to track the *real* problem down!

So, what does the problem look like?

I set up my Core Data stack in the app delegate. Part of that includes connecting to iCloud:

```
    NSURL *storeURL = [[self applicationDocumentsDirectory] URLByAppendingPathComponent:@"XXX.sqlite"];
    NSDictionary *options = @{
                              NSMigratePersistentStoresAutomaticallyOption: @YES,
                              NSInferMappingModelAutomaticallyOption: @YES,
                              NSPersistentStoreUbiquitousContentNameKey : @"XXX"
                              };

    NSError *error = nil;
    _persistentStoreCoordinator = [[NSPersistentStoreCoordinator alloc] initWithManagedObjectModel:[self managedObjectModel]];
    if (![_persistentStoreCoordinator addPersistentStoreWithType:NSSQLiteStoreType
                                                   configuration:nil
                                                             URL:storeURL
                                                         options:options
                                                           error:&error]) {
```

The app delegate passes the managed object context through to the main view controller which then uses it to create a NSFetchedResultsController:

```
    NSFetchRequest *fetchRequest = [[NSFetchRequest alloc] init];
    // Edit the entity name as appropriate.
    NSEntityDescription *entity = [NSEntityDescription entityForName:@"XXX" inManagedObjectContext:self.managedObjectContext];
    [fetchRequest setEntity:entity];

    // Set the batch size to a suitable number.
    [fetchRequest setFetchBatchSize:20];

    // Edit the sort key as appropriate.
    NSSortDescriptor *sortDescriptor = [[NSSortDescriptor alloc] initWithKey:@"someTimestamp" ascending:NO];
    NSArray *sortDescriptors = @[sortDescriptor];

    [fetchRequest setSortDescriptors:sortDescriptors];

    // Edit the section name key path and cache name if appropriate.
    // nil for section name key path means "no sections".
    NSFetchedResultsController *aFetchedResultsController = [[NSFetchedResultsController alloc] initWithFetchRequest:fetchRequest
                                                                                                managedObjectContext:self.managedObjectContext
                                                                                                  sectionNameKeyPath:nil
                                                                                                           cacheName:@"Master"];
    aFetchedResultsController.delegate = self;
    self.fetchedResultsController = aFetchedResultsController;

	NSError *error = nil;
	if (![self.fetchedResultsController performFetch:&error]) {
        // Replace this implementation with code to handle the error appropriately.
        // abort() causes the application to generate a crash log and terminate. You should not use this function in a shipping application, although it may be useful during development.
	    NSLog(@"Unresolved error %@, %@", error, [error userInfo]);
	    abort();
	}
```

(Again, this is pretty much Apple-standard boilerplate code — <s></s> nothing clever going on here.)

But what I found was that when there was already data in iCloud, the records did not automatically appear in the main view controller.

Eventually I found that this was not a threading issue — <s></s>merging the changes into one context and trying to read them from another — <s></s>by adding an explicit fetch request on a “debug” button. Doing this I could see the new data, even though the fetched result controller could not.

In my app delegate I listened for a number of notifications: NSPersistentStoreDidImportUbiquitousContentChangesNotification and NSPersistentStoreCoordinatorStoresWillChangeNotification. My expectation was that NSPersistentStoreCoordinatorStoresWillChangeNotification would fire before switching from the fallback store to the “real” one and NSPersistentStoreDidImportUbiquitousContentChangesNotification would fire when the new data was available.

I was half right. NSPersistentStoreCoordinatorStoresWillChangeNotification fired on a background thread, so I used GCD to ping it onto the main thread and reset the context.

But NSPersistentStoreDidImportUbiquitousContentChangesNotification didn’t fire at all. I guess the objects didn’t change as such, they just became available, which feels like a slightly false distinction to me.

So my next guess was to fire the fetch request again. The data was visible in the main threads context so surely this would find the data?

Nope. (And don’t call me Shirley.)

I was getting pretty lost at this point so I ended up just semi-randomly stopping the code and looking around in the debugger.

And, long story short, I realised that fetch requests have a reference to the persistent store in them — <s></s>check out the affectedStores method. This meant that the NSFetchedResultsController was happily, and correctly, reporting on the empty and no longer used fallback store and completely ignoring the new and fully populated iCloud store.

The simple solution was to listen for the NSPersistentStoreCoordinatorStoresDidChangeNotification and create a completely new fetch request.

```
- (void)storesDidChange:(NSNotification*)notification {
    self.fetchedResultsController = nil;
    [NSFetchedResultsController deleteCacheWithName:@"Master"];
    [self.tableView reloadData];
}
```

(I did think of just adding the new persistent store to the old fetch request but I wasn’t sure that this would create the refresh anyway and, given the frequency with which this is likely to happen, I thought it would be cleaner just to start from scratch.)

These weird problems almost always boil down to just a couple of lines of code. This time was no exception.