---
layout: post
title: Understanding Closures in JavaScript
subtitle: Most powerful feature of JavaScript - Closure
bigimg: /img/path.jpg
---

### 1. What are Closures?  
Closures are the functions that refers to independent variables i.e variables that are used locally but defined in an enclosing scope. In other word a closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain.The closure has three scope chains: it has access to its own scope (variables defined between its curly brackets), it has access to the outer function’s variables, and it has access to the global variables.

Let's take an example [Demo](https://plnkr.co/edit/mnmCs6UIWz0Z6bexkvEy?p=info)

```javascript
function makeFunc() {
	var name = "Jitendra";
  function displayName() {
  	alert(name);
  } 
  return displayName;
}
var myFunc = makeFunc();
myFunc();
```
This piece of code will alert the name "Jitendra" as expected. Interesting thing to notice in this code is makeFunc() returns a function displayeName() before it is executed. We might think once a function makeFunc() is executed, its local variable _name_ cannot be accessed but it is not the case in case of Closure. A variable _myFunc_ has become a closure. A closure is a special kind of object that combines two things: a function, and the environment in which that function was created. The environment consist of any local variables which were in-scope when the closure was created. In this case _myFunc_ is a closure which consist of function _displayName_ and the value of the local variable _name_.

### Example 1

```javascript
  function addNumber(a) {
  	return function(b) {
		return a + b;
	}
  }
  
  var add20 = addNumber(20);
  var add10 = addNumber(10);
  
  console.log("Using closure add20", add20(5)); //logs 25
  console.log("Using closure add10", add10(3)); //logs 13
```
