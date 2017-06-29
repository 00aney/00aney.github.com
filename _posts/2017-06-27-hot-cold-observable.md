---
layout: post
title:  "Hot, Cold Observable"
date:   2017-06-27 15:07:19
categories: [RxSwift]
comments: true
---


<!--more-->

Schedulers
==========

MainScheduler: top of the main thread

```subscribeOn``` switch schedulers.

```observeOn``` changes the scheduler where the observation happens.

Hot Observable(s)
- doesn't have any side-effect during subscription
- does have its own context where events are generated
- sports its own Thread

- use resources whether there are subscribers or not
- produce elements whether there are subscribers or not
- are primarily used with stateful types such as ```variable```.

Cold Observable(s)
- doesn't produce any elements before any observers subscribe to it.

- only consume resources upon subscription
- only produce resources upon subscription
- are primarily used for async operations such as ```networking```.
