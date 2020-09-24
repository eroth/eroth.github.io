---
date: 2020-09-23 03:29:55+00:00
title: KeepMyFood iOS app released
header:
  image: /assets/images/posts/2020-09-23-keep-my-food-released/header.png
teaser_image_path: /assets/images/posts/2020-09-23-keep-my-food-released/teaser.png
view_hierarchy_gallery:
  - url: /assets/images/posts/2020-09-23-keep-my-food-released/keep_my_food_ipad.png
    image_path: /assets/images/posts/2020-09-23-keep-my-food-released/keep_my_food_ipad.png
    alt: "Screenshot of the KeepMyFood iPad view hierarchy"
    title: "KeepMyFood iPad screenshot"
  - url: /assets/images/posts/2020-09-23-keep-my-food-released/keep_my_food_iphone.png
    image_path: /assets/images/posts/2020-09-23-keep-my-food-released/keep_my_food_iphone.png
    alt: "Screenshot of the KeepMyFood iPhone view hierarchy"
    title: "KeepMyFood iPhone screenshot"
tags:
- iOS
- RxSwift
- Firebase
- Swift
---

To all my millions of readers, I have an announcement to make: My first iOS app, "KeepMyFood," was recently released and [is now available](https://apps.apple.com/us/app/keepmyfood-food-organizer/id1531074104) on the iOS App Store! The aim of it is to help people manage all the food in their household, which is typically in a variety of locations: refrigerator, pantry, freezer, etc.

Time and time again, I'd seen in our own household how we'd oftentimes forget we had food only to realize down the line that it had gone off.  Not to mention all the times we'd purchased doubles of food we already had! And of course there are the [environmental costs](https://moveforhunger.org/the-environmental-impact-of-food-waste) of food waste made more awful and ironic by the amount of people dying of starvation or malnutrition.

As can be imagined, there are a ton of features that could be added in an app like this: barcode scanning of food UPC labels, integrations with third party APIs, etc., so the real challenge for me was deciding what features I should include in `v1.0` and what should constitute an MVP for my idea.  Not having had any product management experience, this was a great exercise because as developers it's quite easy for us to keep _developing_ away.  We can be like the [Energizer Bunny](https://en.wikipedia.org/wiki/Energizer_Bunny) sometimes (does anyone else know this reference??).  I tried to approach this project from as organized a fashion as I could, as I wanted it to be well-thought-out and planned.  I'd like to go through a little of my approach in this post.

## Requirements
The first thing I did was to define my requirements.  For the `v1.0` release, I wanted the app to:
* Have persistent storage, sync across devices, and to allow multiple users to collaborate together (this is important because there are typically multiple people in a household that would be sharing food)
* Allow users to create and edit virtual "spaces" that would correspond to food storage locations (refrigerator, pantry, etc.)
* Allow users to add, edit, and show details of all the foods that are in their spaces
* Have some kind of basic account management screen
* Be able to create an account, log in to their account, reset their password, and delete their account (we know no one would ever want to do this but we still have to provide an option)

## Organization
Having come from using Jira at the past few companies I worked at, I was looking for a similar tool to help keep track of my user stories and progress.  I had used Trello briefly at a contracting gig I'd taken on a while ago and, while not nearly as fully featured as Jira was, the price was right: free! After using it much more this time around than the last time I'd used it, I found it to be highly customizable and configurable to suit one's needs.  I set up three "lists" to keep track of my backlog, items in progress, and items that had been finished, and off I went!

## Persistent Storage
For services that were pretty turn-key and would allow me to do the things I listed above without any kind of backend, there were really only two options that came to mind: `Core Data` with `CloudKit` or `Firebase`.  I would have like to have used `Core Data` & `CloudKit`, but after some initial exploration of the syncing aspect it seemed that it was somewhat clunky and relied on notifications (there were also a few other quirks that I don't recall at the moment).

It's a shame because I was long overdue for a re~~match~~visit with this library that had caused me quite a few pains in the past (probably entirely owing to my ineptitude at the time, I'm sure).  `Firebase`, while not without its faults and idiosyncrasies, seemed to handle syncing across multiple users and devices pretty seamlessly and easily, without hardly any setup overhead.  It was this feature (coupled with its NoSQL database approach and other backend-related services it offers) that eventually won me over.

Not sure if I will ever get this far with it, but you can also write cloud functions to approximate backend services.  Note: If you decide to use `Firebase`, start by incorporating the [security rules](https://firebase.google.com/docs/rules) into your database design! I can assure you from experience it will save you loads of trouble down the road.

## View Hierarchy
Due to the master-detail relationship of the data I was presenting (spaces->foods), the `UISplitViewController` was the obvious choice.  Not only is it built for this type of thing; it is also perfect for developing universal iPad/iPhone apps, as it can be readily configured to show two columns on regular width devices (e.g., iPad) while acting like a stock `UINavigationController` on compact width devices (e.g., iPhone).

After I realized I'd need to add a user account section, I then decided to use a `UITabBarController` so users could toggle between their spaces/foods and their user account.  This led to my embedding the split view controller inside the tab bar controller, which worked out well.

{% include gallery id="view_hierarchy_gallery" caption="*KeepMyFood iPad & iPhone screenshots—this is the same `UISplitViewController`.*" %}

## Views
My view (pun intended) of how I was going to present the user's food list has changed over time.  Initially, I was going to allow the user to take a picture of a food and thus I was thinking I would model the UI off of Apple's Photos app.  It uses a `UICollectionView` and `UICollectionViewCell` (of course, I can't be 100% certain but I feel pretty confident).  However, after building out this UI, I decided to switch to a `UITableView` instead for several reasons.  I had decided against including food images in this first release, much more information could be displayed using `UITableViewCell`, and the table view comes with deletion actions/UI out of the box.

## Libraries
In addition to `Firebase`, I make heavy use of `RxSwift` in "KeepMyFood." As `Firebase`'s API makes use of a sockets approach (one sets up a connection to a node in one's database, and this connection sends through changes to this node and its children based on the types of events the client signs up to receive), I thought it lent itself well to the events-based, streaming approach of `RxSwift`.  I will expand upon this more in a later post, but I built a `Firebase` API client to centralize all its operations (reads, writes, deletions, etc.) and these methods returned `Observable` objects.

There are also a few other libraries used, but they're more around various UI helpers like [NotificationBanner](https://github.com/Daltron/NotificationBanner) (used for displaying notification banners when the user logs out, deletes their account, or there's been an error) and [SVProgressHUD](https://github.com/SVProgressHUD/SVProgressHUD) (used for displaying an activity spinner).

Thank you for reading, and I look forward to sharing more in-depth details of my process and implementation in future posts! As always, feel free to leave any comments below.
