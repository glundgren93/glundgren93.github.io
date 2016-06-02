---
layout: post
title: First Class Functions in JavaScript
---

Functions in JavaScript are considered first class. What that means is that they can do all the things a normal object can do. Just like any other variable.

* They can be stored in a variable:

```javascript
var sing = function() {
  return 'singing a song';
}

sing(); // singing a song
```

* They can be stored in an array slot:

```javascript
var singManySongs = [
  'song a',
   function() {
     return 'song b';
   }  
];

singManySongs[1](); // song b
```

* They can be stored in an object property:

```javascript

var singingObject = {
  songA: 'singing A',
  songB: function() {
    return 'singing B';
  }
};

singingObject.songB(); // singing B
```

* They can be created as needed:

```javascript

(function() { return 'singing '; })() + 'nice song'; // singing nice song
```

* They can be passed to a function:

```javascript

function sing(fn, song) {
  return fn() + song;
}

sing(function() { return 'singing ' }, 'this song'); // singing this song
```

* They can be returned from a function:

```javascript

function singASong() {
  return function() {
    return 'singing a Song';
  }
}

var sing = singASong();
sing(); // singing a Song
```
