---
date: 2015-06-20 03:29:55+00:00
last_modified_at: 2018-05-25 03:29:55+00:00
title: "ERJustifiedFlowLayout for iOS"
header:
  image: /assets/images/posts/2015-06-20-erjustifiedflowlayout-for-ios/eroth-flowlayout-post-feature.png
teaser_image_path: /assets/images/posts/2015-06-20-erjustifiedflowlayout-for-ios/teaser.png
gallery:
  - url: /assets/images/posts/2015-06-20-erjustifiedflowlayout-for-ios/left-justified.png
    image_path: /assets/images/posts/2015-06-20-erjustifiedflowlayout-for-ios/left-justified.png
    alt: "Screenshot showing left justification mode of ERJustifiedFlowLayout"
    title: "Left justification"
  - url: /assets/images/posts/2015-06-20-erjustifiedflowlayout-for-ios/right-justified.png
    image_path: /assets/images/posts/2015-06-20-erjustifiedflowlayout-for-ios/right-justified.png
    alt: "Screenshot showing right justification mode of ERJustifiedFlowLayout"
    title: "Right justification"
tags:
  - iOS
  - UIKit
  - UICollectionView
  - Open Source
---

I recently finished my first open source project—[ERJustifiedFlowLayout](https://github.com/eroth/ERJustifiedFlowLayout) (link to project on GitHub)! It's a tool for an iOS [`UICollectionView`](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UICollectionView_class/), which is an incredibly versatile and powerful tool to display cell, row, or column content.  It uses a subclass of a `UICollectionViewFlowLayout`, which tells the collection view how to lay out its cells.

My library allows one to perform horizontal left or right justification (center coming soon) with cell content (including variably sized cells), plus stipulate a fixed distance between cells—something that isn't possible with Apple's out-of-the-box Flow layout.  I also plan on adding vertical justification (top, center, bottom).

Here's a few screenshots of it in action:

{% include gallery caption="*Left and right justification on `ERJustifiedFlowLayout`.*" %}

There's a full tutorial on how to use it at the GitHub repo, as well as lots more screenshots.  Enjoy!
