---
id: 1960
title: 'iPhone Dev: Saving State'
date: '2010-02-16T19:20:24+00:00'
author: 'Stephen Darlington'
excerpt: 'A good iPhone application should launch in the same state it was in when it was last closed. Here''s how I do it in my apps.'
layout: post
guid: 'http://www.zx81.org.uk/?p=1960'
permalink: /computing/software/iphone-dev-saving-state.html
adman_disable:
    - 'on'
categories:
    - Software
tags:
    - apple
    - code
    - development
    - iphone
---

I see every now and again that [Apple needs to make it easier to allow developers to save the state of their application](http://db.tidbits.com/article/10989) so that they open up exactly as they were when they were shut down.

Obviously I’m all for Apple making my life easy, but that’s not going to happen for a while yet so I thought I’d share how I implemented it in [Yummy](http://www.yummyapp.com/).

The key is this simple protocol:

```

@protocol SaveState

- (NSData*) saveState;
- (id) initWithSaveState:(NSData*)data;

@end

```

This is what I have in my `applicationWillTerminate:` method:

```

NSMutableArray* vcList = [NSMutableArray arrayWithCapacity:3];
for (UIViewController* vc in self.navigationController.viewControllers) {
    // Classes that don't implement the SaveState protocol will be ignored
    if ([vc conformsToProtocol:@protocol(SaveState)]) {
        NSArray* state = [NSArray arrayWithObjects:NSStringFromClass([vc class]),
                                                                     [(UIViewController<savestate>*)vc saveState],
                                                                     nil];
        [vcList addObject:state];
    }
}
</savestate>
```

This is in the `applicationDidFinishLaunching:`:

```

for (NSArray* screen in screenList) {
    UIViewController<savestate>* next =
                [[NSClassFromString([screen objectAtIndex:0]) alloc]
                                   initWithSaveState:([screen count] == 2) ?
                                   [screen objectAtIndex:1] : nil];
    if (next != nil) {
        [[self navigationController] pushViewController:next animated:NO];
        [next release];
    }
}
</savestate>
```

So a simple example, for a view controller that needed to be remembered but didn’t need to store any extra state, would be:

```

- (NSData*) saveState {
    return nil;
}

- (id) initWithSaveState:(NSData*)data {
    return [self init];
}

```

But you can initialise each view controller with anything that can be converted into an NSData. (I picked NSData rather than, say, id because an NSData can always be serialised. Made sense to make that assumption.)

One weakness is that it doesn’t cope with the situation where a modal view is on top but that should be pretty easy to implement if it’s important (it generally isn’t in Yummy).