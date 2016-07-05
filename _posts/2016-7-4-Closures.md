---
layout: post
title: Closures
---

 # What is a Closure?

 "Closure is when a function remembers the variables around it even when that function is executed elsewhere."

If we declare variables inside a function and return another function that uses the variables created, we are using closures.

A closure can look like the following piece of code:

 ```javascript
 const whatWasTheVariable = () => {
   const variable = 'i am a variable'; // Captured by closure

   return function() {
     return "The variable was: " + variable;
   };
 }

 var reportVariable = whatWasTheVariable();
 reportVariable(); // The variable was: i am a variable

 ```


 The above function exposes (returns) another function. When we assign the function to a variable, the variable will become the exposed function.
 Even though the outer function has returned, the inner function still has acccess to the variables inside the outer function scope.


 # Data Privacy

 Closures are one way to enable data privacy in Javascript. You can't access the data from an outside scope except through methods defined within the closure scope.

 ```javascript
 var pingpong = (function() {
   var PRIVATE = 0;

   return {
     inc: function(n) {
       return PRIVATE += n;
     },
     dec: function(n) {
       return PRIVATE -= n;
     }
   };
 })();

 pingpong.inc(10); // 10
 pingpong.dec(2); // 8


 ```

 The only way to modify the PRIVATE variable is through the use of the methods inc and dec, which are defined in the closure scope.
