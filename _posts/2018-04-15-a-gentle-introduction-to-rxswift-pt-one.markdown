---
date: 2018-04-15 03:29:55+00:00
modified: 2018-04-15 03:29:55+00:00
title: A Gentle Introduction to RxSwift, Part 1
header:
  image: /assets/images/posts/2018-04-15-a-gentle-introduction-to-rxswift-pt-one/rxswift-introduction-feature.png
teaser_image_path: /assets/images/posts/2018-04-15-a-gentle-introduction-to-rxswift-pt-one/teaser.png
tags:
  - iOS
  - RxSwift
  - Reactive Programming
---

In late 2017, I started an iOS developer position in London that required my learning [RxSwift](https://github.com/ReactiveX/RxSwift).  At the time, it was a pretty foreign concept to me—I'd heard buzzwords like "Reactive programming" and "Rx" tossed around, and had done some research on what the concepts were, but even after reading about them it all seemed opaque and somewhat grandiose.  And it felt like a paradigm shift in thinking about how objects communicated with each other and in how I wrote code.

When I first started at this position, I was handed a copy of what my coworkers affectionately referred to as "The Bible"—a copy of [RxSwift: Reactive Programming with Swift](https://store.raywenderlich.com/products/rxswift), (published by Razeware LLC aka Ray Wenderlich; the darlings of the iOS tutorial and resource space)—and given about two weeks to go through it.  Although I think the book was written very well, and that it was a tremendous aid to my learning RxSwift, it was still a *lot* to absorb.  Complicating things further was that the app I was working on had implemented RxSwift in a variety of different ways, which made perfect sense considering that the developers that had worked on it had themselves been learning RxSwift as they'd been coding it! Of course, I also perused numerous blog tutorials written by people trying to help others in my boat, but sometimes that served only to add additional complexity as there is usually more than one way to skin a cat, and until one knows what one is doing others' approaches may be confusing or complicate things further.

I'm not sure if this combination caused me to have problems, or if it was just the legitimate learning curve around RxSwift (given the abundance of how-do-I-do-this-in-RxSwift posts on Stack Overflow, that could definitely be a possibility!), but I feel like it took me a while to *get* RxSwift.  Not to just understand the concepts behind it, but to be able to be assigned a feature and start using it almost as naturally as one would use Swift itself to write classes and objects to handle the feature's various responsibilities and requirements.  Through all this, I experienced lots of frustration and moments of "how do I get this to work?!" and "what is going on in this code I'm reading??" I also experienced moments where I thought I'd gotten a decent grip on it all, only to realize I hadn't and that I actually had a fundamental misunderstanding of some of the core concepts!

In retrospect, it's taken about four months for me to reach this point and, as anyone who is remotely introspective or self-aware is wont to do, I started to think back on my learning process and what threw me curveballs during it.  I came up with a few thoughts and ideas around the kinds of explanations of RxSwift I wished I'd seen out there, as well as what had confused me amongst everything I'd seen, and decided to write this post in an attempt to help others.  If you're reading this and feel the way I indicated I felt as I was learning it, don't give up hope! Take it slow and know that it *is* complicated, it's fast-changing, and it involves a very different way of looking at things than most iOS developers will be accustomed to! But once you "get it" you will start to look at your code and app architecture in a very different way.  Even if you don't end up using RxSwift or don't like it, as developers we must always push ourselves to stay current and abreast of new technologies and developments as much as we can.  The languages, tools, and paradigms we use are as iterative as the code we write.

Please stay tuned for the next post (coming soon!), which will drill down a little more into the specifics I mentioned.  In the meantime, please feel free to leave any comments below!
