---
date: 2019-03-17 03:29:55+00:00
title: A Gentle Introduction to RxSwift, Part 2
header:
  image: /assets/images/posts/2019-03-17-a-gentle-introduction-to-rxswift-part-two/feature.png
teaser_image_path: /assets/images/posts/2019-03-17-a-gentle-introduction-to-rxswift-part-two/teaser.png
tags:
- iOS
- RxSwift
- Reactive Programming
- Swift
---

Ok, so it's been a little while since I wrote the [initial post]({{ site.baseurl }}{% post_url 2018-04-15-a-gentle-introduction-to-rxswift-pt-one %}) for this series on `RxSwift`, entitled "A Gentle Introduction to RxSwift, Part 1." Almost a year, in fact! But that's the great thing about doing a blog—you get to write what you want when you want!

In any case, here we are and it's time for the next installment of this series! I figured the easiest introduction to how `RxSwift` works would be a side-by-side comparison to a design pattern that every iOS developer should be familiar with: closures (AKA blocks, if you're coming from an Objective-C background).  At its simplest, `RxSwift` can be used in much the same way, and this article will attempt to establish a connection between the two.  It's my hope that this will foster some familiarity between something that can be daunting (`RxSwift`) and something that should be commonplace (closures).

One main difference between closures and observables (a fundamental type in `RxSwift`) is that closures are typically used to deliver a single result (e.g., an API call completed with a response, a view controller finished performing a dismiss operation, etc.), while observables deliver a stream of results.  It's like plugging your lamp into the electrical outlet and getting a continuous flow of electricity that powers the light, or akin to turning on a garden hose and seeing water come out.

Without further ado, let's jump in! Below is a basic example of how one might use a closure:

{% gist d1895984bee8bee11c5f4ba83f3d0bc0 %}

In this example, we have a function that takes a closure for its `completed` argument—a closure which has a `String` argument.  The idea is to model calling a function with a closure argument that returns a result after some operation is completed (this example is rather contrived because we'd also want to do something if there was an error).  We then call the function (using trailing closure syntax) and when its `completed` argument is called we print out the result of our extremely quick operation.  Of course, we could've also called our function so, using shorthand argument names:

`doSomethingClosure { print("result: \($0)") }`

Now, for the `RxSwift` equivalent of the above closure example:

{% gist 0e23c881c5a4458353a265ec7f1ef24c %}

What's going on here? In plain English, instead of passing in a closure argument to the `doSomethingRx()` function, we're returning an object which allows us to know when our function has done something; i.e., it provides us updates that we send.

In `Rx` lingo, we're first creating an object called an `Observable` (of type `String`) in a factory function called `create()`.  Its signature is:
```
public static func create(_ subscribe: @escaping (RxSwift.AnyObserver<Self.E>) -> Disposable) -> RxSwift.Observable<Self.E>
```
As can be seen, this function takes a closure called `subscribe` as a parameter which has an object called an `AnyObserver` (of the same type the observable is; in this case a `String`) as an argument. We then use this observer to send or *emit* events that we want to receive.  But in order to know about our observable's updates we have to *subscribe* to that observable, which allows us to receive data whenever it emits events.  A *subscription* is just saying, "We want to know whenever this thing does something and every time it does we'll receive an update."

It's the equivalent of plugging the lamp plug into the electrical outlet or turning on the garden hose, to use the earlier examples.  The `disposeBag` property you see (of type `DisposeBag`) is how `RxSwift` deals with breaking retain cycles on its objects—it deallocates the observable when its owning object is deallocated.

Just like with the closure examples, we could have also done:
```
doSomethingRx()
    .subscribe(onNext: { print("result: \($0)") })
    .disposed(by: disposeBag)
```

Unfortunately, you won't see much of the aforementioned streaming action here—as our observable is only returning one event for this example—but imagine we had multiple requests coming from that function.  You would receive our `"result: We're using RxSwift!"` message each time a request completed.  A future post (hopefully, not too far in the future) will cover that in much more detail!  Of course, you could also use closures to accomplish the same thing, but as you'll see (if you start to use `RxSwift`) its power lies in its higher-order functions (called *operators*), the nuances of control it offers you, and its integration with `UIKit` via `RxCocoa`.

As with any choice in design patterns or architecture, there are pros and cons to every decision we make as developers.  Some projects may be suited to using RxSwift and some may not!

[Link to playground](https://github.com/eroth/2019-03-17-RxSwift-Closures)

[Post pull requests](https://github.com/eroth/eroth.github.io/blob/develop/_posts/2019-03-17-a-gentle-introduction-to-rxswift-part-two.markdown)

`Xcode 10 / iOS 12 / RxSwift 4.3.1`
