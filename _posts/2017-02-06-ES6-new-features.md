---
layout: post
title: What's new in ECMAScript6 (ES6)?
subtitle: Comparision between ES5 and ES6 features.
---

This post contains the list of new features introduced in ES6. Similarly, we will go through the syntax used in ES5 side by side with ES6.

#### Classes

#### Modules

#### const and let 

#### Arrows functions

#### Default Parameters

```javascript
//ES5 Style
var changeColor = function(color) {
  var marioColor = color || 'red';
  
  this.css({
    background-color: marioColor;
  });
}
//ES6 Style
var changeColor = function(color = 'red') {
  var marioColor = color ;
  
  this.css({
    background-color: marioColor;
  });
}

//Calling function
changeColor();

```
