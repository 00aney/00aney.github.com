---
layout: post
title:  "Custom Operator"
date:   2017-07-11 15:07:19
categories: [Swift]
comments: true
---


<!--more-->

Custom Operator
---------------
- Name
- Arity and Position 인수, 위치
- Precedence 상위
- Associativity 연관성

prefix, postfix, infix operator

```swift
extension CGPoint {
  static func *(lhs: CGPoint, rhs: CGAffineTransform) -> CGPoint {
    return lhs.applying(rhs)
  }

  static prefix func -(input: CGPoint) -> CGPoint {
    return CGPoint(x: -input.x, y: -input.y)
  }
}

extension CGAffineTransform {
  static func *(lhs: CGAffineTransform, rhs: CGAffineTransform) -> CGAffineTransform {
    return lhs.concatenating(rhs)
  }
}

func *(points: [CGPoint], transform: CGAffineTransform) -> [CGPoint] {
  return points.map{ $0 * transform }
}

```

Auto Closure
------------

- This attribute is used to delay the evaluation of an expression by automatically wrapping that expression in a closure with no arguments
- Autoclosure argument type must be '()'


```swift
infix operator !!: NilCoalescingPrecedence

func !!<Wrapped>(optional: Wrapped?, fatal: @autoclosure () -> Never) -> Wrapped {
  guard let unwrapped = optional else {
    fatal()
  }

  return unwrapped
}
let value = fullValue !! fatalError("no value when one was expected")
let value2 = fullValue !! { fatalError("no value when one was expected") }
```

Short Circuiting, Deferred execution
```swift
extension Bool {
  static func &&(lhs: Bool, rhs: @autoclosure () -> Bool) -> Bool
}
```

Precedence Group
----------------

```swift
precedencegroup ExponentiationPrecedence {
  higherThan: MultiplicationPrecedence
  associativity: none   // you must use parenthesis
}

infix operator **: ExponentiationPrecedence

func **(base: Double, exponent: Double) -> Double {
  return pow(base, exponent)
}
```

Ref
---
https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/AdvancedOperators.html

https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/AdvancedOperators.html#//apple_ref/doc/uid/TP40014097-CH27-ID41

https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/Declarations.html#//apple_ref/doc/uid/TP40014097-CH34-ID380

https://github.com/apple/swift-evolution/blob/master/proposals/0077-operator-precedence.md
