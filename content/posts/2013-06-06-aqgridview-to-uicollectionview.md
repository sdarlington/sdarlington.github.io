---
id: 3646
title: 'AQGridView to UICollectionView'
date: '2013-06-06T20:30:59+01:00'
author: 'Stephen Darlington'
layout: post
guid: 'http://www.zx81.org.uk/?p=3646'
permalink: /computing/opinion/aqgridview-to-uicollectionview.html
categories:
    - Opinion
---

I recently [moved a code base from using AQGridView — a third party library — to UICollectionView](https://github.com/sdarlington/baker/commit/1becbac8dd81532140ac8fe1d74f52e19c0558d7 "https://github.com/sdarlington/baker/commit/1becbac8dd81532140ac8fe1d74f52e19c0558d7"). I have nothing against third party components but I’m a big fan of minimising dependencies and reducing the amount of code that need to be understood. In this case I managed to remove about 5000 lines of code from the project. Switching to the UIKit version made sense on both counts.

Both components do more or less the same thing and their APIs fortunately look pretty similar. (UICollectionView can be coerced into doing a lot more but we just need it for a simple grid.) Most of the changes are just renaming methods; I was surprised how little new code needed to be written.

Creating the grid is easy enough, but you need to specify more information up-front:

```
-    self.gridView = [[AQGridView alloc] init];

``````
+    self.gridView = [[UICollectionView alloc] initWithFrame:CGRectZero collectionViewLayout:[[[UICollectionViewFlowLayout alloc] init] autorelease]];

```

(I also took the opportunity to fix a memory leak in the original project.)

One thing that caught me out initially, is that you need to register the classes you’re going to use as cells before you use them:

```
+    [self.gridView registerClass:[UICollectionViewCell class] forCellWithReuseIdentifier:@"cellIdentifier"];

```

Creating the cell looks pretty similar:

```
-    AQGridViewCell *cell = (AQGridViewCell *)[self.gridView dequeueReusableCellWithIdentifier:cellIdentifier];

``````
+    UICollectionViewCell* cell = [self.gridView dequeueReusableCellWithReuseIdentifier:cellIdentifier forIndexPath:indexPath];

```

And configuring the cell actually takes slightly less work using a UICollectionView:

```
-    cell = [[[AQGridViewCell alloc] initWithFrame:cellFrame reuseIdentifier:cellIdentifier] autorelease];

``````
-    cell.selectionStyle = AQGridViewCellSelectionStyleNone;

``````
+    UICollectionViewCell* cell = [[[UICollectionViewCell alloc] initWithFrame:cellFrame] autorelease];

```

The rest is mostly renaming delegate methods:

| ``` AQGridView ``` | ``` UICollectionView ``` |
|---|---|
| ``` numberOfItemsInGridView: ``` | ``` numberOfSectionsInCollectionView: ``` |
| ``` gridView:cellForItemAtIndex: ``` | ``` collectionView:cellForItemAtIndexPath: ``` |
| ``` portraitGridCellSizeForGridView: ``` | ``` collectionView:layout:sizeForItemAtIndexPath: ``` |
| ``` gridView:didSelectItemAtIndex: ``` | ``` collectionView:didSelectItemAtIndexPath: ``` |

There are two other “gotchas,” one easy and one hard.

Inside a UICollectionView, multiple updates need to be grouped together in a block and called using the `performBatchUpdates:completion:` method. (Oh, and the `insertItemsAtIndices:withAnimation:` method becomes `insertItemsAtIndexPaths:`.)

The last one is about formatting. AQGridView centres cells. UICollectionView, on the other hand, pushes the cells to the far left or right of the frame. This is probably easier to explain with a picture. This is the how UICollectionView flows the cells by default:

<figure aria-describedby="caption-attachment-3652" class="wp-caption aligncenter" id="attachment_3652" style="width: 300px">[![Outer Cells](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2013/06/Screen-Shot-2013-06-06-at-20.00.31-300x249.png?resize=300%2C249)](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2013/06/Screen-Shot-2013-06-06-at-20.00.31.png)<figcaption class="wp-caption-text" id="caption-attachment-3652">Outer Cells</figcaption></figure>

And this is how we want it to look, and how it does look using AQGridView:

<figure aria-describedby="caption-attachment-3653" class="wp-caption aligncenter" id="attachment_3653" style="width: 300px">![Centred Cells](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2013/06/Screen-Shot-2013-06-06-at-20.01.16-300x249.png?resize=300%2C249)<figcaption class="wp-caption-text" id="caption-attachment-3653">Centred Cells</figcaption></figure>

Now the *correct* way of dealing with this would be to build a custom `UICollectionViewFlowControl`, which is the way you can definine custom layouts. That seemed like a lot of work just to centre a few cells! [Instead I dynamically adjusted the frame on rotation](https://github.com/sdarlington/baker/commit/aac30b761388bad98c56c2b9db7f5c56ab5b5db6 "https://github.com/sdarlington/baker/commit/aac30b761388bad98c56c2b9db7f5c56ab5b5db6") which gives the *appearance* of centring the cells without most of the hard work. May be one day I’ll get around to doing the job correctly!

If the formatting has made some of this difficult to follow, you can see the [full patch on GitHub](https://github.com/Simbul/baker/pull/818).

Overall, the process of converting from `AQGridView` to `UICollectionView` was straightforward, which I think is a testament to the quality of the original component. Next time I’m aim to remove a lower quality, more problematic piece of code!