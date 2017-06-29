---
layout: post
title:  "1. Error Handling in RxSwift"
date:   2017-06-26 15:07:19
categories: [RxSwift]
comments: true
---
Errors are an inevitable part of any application. Unfortunately, no one can guarantee an application will never error out, so you will always need some type of error-handling mechanism.

<!--more-->

Some of the most common errors in applications
----------------------------------------------
- No internet connection
- Invalid input
- API error or HTTP error

Error can be handled in two ways
--------------------------------
- catch
- retry

Handle error with catch
-----------------------
catch functions
```swift
func catchError(_ handler:) -> RxSwift.Observable<Self.E>

func catchErrorJustReturn(_ element:) -> RxSwift.Observable<Self.E>
```


Handle error with retrying
--------------------------
- A retry operator repeats `the entire task` inside the observable

Retry operators
```swift
func retry() -> RxSwift.Obsearvable<Self.E>

func retry(_ maxAttemptCount:) -> Observable<E>

func retryWhen(_ notificationHandler:) -> Observable<E>
```
