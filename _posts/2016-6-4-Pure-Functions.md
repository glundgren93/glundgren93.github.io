---
layout: post
title: Pure Functions in JavaScript
---

Reducing or eliminating mutation of state change in our progams is a way of lowering the complexity of softwares. Pure functions are one way of achieving this.

A pure function doesn't change the state outside of its body. Its result is calculated from the values of the arguments given to it. Given the same arguments, pure functions will always return the same output, because its execution doesn't depend on the the state of the system.


```javascript

class Point {
  constructor(x, y) {
    this._x = x;
    this._y = y;
  }

  // methods don't modify anything
  // they return fresh instances of Point
  withX(val) {
    return new Point(val, this._y);
  }

  withY(val) {
    return new Point(this._x, val);
  }
}

// We defined p as a Point with 0,1
var p = new Point(0, 1);

// Even though we are saying that the x is 1000
// once we call p again, x won't have changed its value.
p.withX(1000); // {_x: 1000, _y: 1 }

p; // {_x: 0, _y: 1 }
```
