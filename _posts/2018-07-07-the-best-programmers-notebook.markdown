---
date: 2018-07-07 03:29:55+00:00
title: Quiver—The Best Programmer's Notebook
header:
  image: /assets/images/posts/2018-07-07-the-best-programmers-notebook/feature.png
teaser_image_path: /assets/images/posts/2018-07-07-the-best-programmers-notebook/teaser.png
gallery:
  - url: /assets/images/posts/2018-07-07-the-best-programmers-notebook/quiver-screenshot.png
    image_path: /assets/images/posts/2018-07-07-the-best-programmers-notebook/quiver-screenshot.png
    alt: "Screenshot showing a Quiver notebook"
    title: "Quiver notebook screenshot"
chrome_bookmarks_screenshot:
  - url: /assets/images/posts/2018-07-07-the-best-programmers-notebook/chrome-bookmarks-structure.png
    image_path: /assets/images/posts/2018-07-07-the-best-programmers-notebook/chrome-bookmarks-structure.png
    alt: "Screenshot showing a lot of web bookmarks in Chrome"
    title: "Ridiculous amounts of bookmarks in Chrome"
tags:
  - Notebooks
---

For a number of years, I've been accumulating tons of bookmarks in Google Chrome.  For the most part, how I've been using them is ok—I usually have them organized by a particular topic or a particular software library.  For example, for my iOS bookmarks, I have a whole folder for `UIKit` and then subfolders for each interface object (`UITableView`, `UIStackView`, etc.).  I also have folders for specific iOS topics, like network operations, device rotation, keychain access, etc.  This sort of works ok, as for anything `UITableView`-related I go to the folder for it and look through all the bookmarks there.  Or I do a search through my bookmarks.

{% include gallery id="chrome_bookmarks_screenshot" caption="*Ridiculous amounts of bookmarks in Chrome.*" %}

But one thing I started noticing is that I wanted to make *notes* on some of these bookmarks.  Like when you find a solution for something but it only works on one OS version and does something entirely different in another! As I thought about it more, I realized I wanted to be able to write short tutorials on topics or code.  Or to be able to annotate gists.  But I wanted it to be only visible to myself.

At first, I tried to see if I could make this work in Chrome—I looked at a few extensions that would let you make notes on your bookmarks, but they didn't work.  I then came to the conclusion that what I really wanted was to sort of have an internal blog or notebook!

So, my requirements were:
* It had to support tags
* Had to be accessible on mobile or web (the former through a dedicated app or at least be mobile-friendly)
* Had to support inline code blocks (ideally [gists](https://gist.github.com))
* Had to support and sync attachments (so I could attach sample projects or files)
* Markdown is a plus
* Open source and/or free would be great
* Had to be quick and easy to add entries

As I'd been using [Evernote](https://evernote.com/) for years, I first tried to use it for these purposes.  It syncs attachments and has tags, so I starting researching adding code blocks or gists.  It turns out there is no gist support (which kind of makes sense, although I feel like they could integrate it if they really wanted to) and no out-of-the-box way to add code blocks (as well as no markdown support).  The lack of markdown support is incredible and their forums are full of people complaining about these features being missing.  The closest thing I could find in the way of adding code blocks is to go to another site that will format it (like <http://highlight.hohli.com/>), then copy/paste it to Evernote.  Ugh.

I also thought of using Apple's [Notes](https://support.apple.com/en-gb/ht205773) app, but same above issue (although, it does let you attach files now).  Still, not very programmer-friendly and it doesn't support tags.  Then, I started looking in earnest at other solutions.  I first thought about creating an internal blog—sort of like this one but just for myself.  It hit all the things I was looking for, except the last point of it being quick and easy to add entries.  In order to make a new post, I have to create a new branch in Git, fire up a text editor, write the post, commit it in Git, and then merge it back in to my deployment branch.  Hardly a quick and easy way to make notes on the fly! I did look into automating this whole process somewhat but then started looking into programmer notebooks.  I wanted something integrated that I could just dash out quick notes with links and/or attachments in it.

This is what I looked at:
* [Boostnote](https://boostnote.io/)—open source, which I liked, but at the time of this writing it didn't support attachments; although, it has tags, a mobile app, and markdown support
* [Bear](http://www.bear-writer.com/)—didn't support compressed file attachments at the time of this writing, but has code block support; charges for syncing across devices
* Some other service that imports your Github gists and allows you to annotate them
* [Quiver](http://happenapps.com/#quiver)—what I eventually went with!

{% include gallery caption="*Screenshot of Quiver from their site.*" %}

Surprisingly, I wasn't able to find something that did everything I wanted—but Quiver was the best of what I saw! Here are the main points:

* It costs $9.99 but they offer a no-time-limit trial version that allows you to test-drive it; it's Mac only
* They also have a mobile app (iOS only)
* It has markdown support, code block support (with language highlighting options), and syncing (via Dropbox or most major cloud syncing services)
* Their notebooks work on the concept of "cells" that allow you to insert different types of content: text, markdown, code, LaTex, or diagrams
* You can add most kinds of attachments (including file attachments)
* Mobile app allows you to share notes via emailing markdown or plain text

A few of the negatives/areas to improve:
* Not very good documentation on how to configure with Dropbox
* Mobile app doesn't allow you to view attachments
* Mobile app in general could be improved

But, overall, this one was a winner for me! I've been using it for the past few months and don't have any major complaints.  The only thing I haven't quite decided on is the notebook/tag structure.  At the moment, I have notebooks for general topics (iOS, Ruby, etc.) and then I use tags for each post.  However, I'm also tagging each post in my iOS notebook with an `iOS` tag, so it remains to be seen whether using notebooks at all is really necessary for how I use it (probably is).  Please leave any comments/questions below!
