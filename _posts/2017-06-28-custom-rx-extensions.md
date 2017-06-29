---
layout: post
title:  "Custom Rx Extensions"
date:   2017-06-28 15:07:19
categories: [RxSwift]
comments: true
---


<!--more-->

Custom Reactive Extensions
==========================


```swift
extension Reactive where Base: [className] {
  // TODO: create wrapper methods
  // return an Observable
}
```

Example
-------
extension URLSession


The SingleAssignmentDisposable() will ensure only one subscription is ever alive at a given time for every single cell so you won’t bleed resources.
