---
layout: post
title: How to access arguments inside an empty function in JS?
subtitle: Importance of keywork _arguments_
bigimg: /img/path.jpg
---

### 1.How to access arguments inside an empty function in JS? 
Eventhough the function declared is an empty function, we can pass the arguments to that function and access those arguments inside
an empty function, simply by using keyword _arguments_.

For example

```javascript
var car = function() {
  console.log("Arguments of this function are: ", arguments);
};

car("Wheel","Enginee","Glass");
//Executing above code logs: ["Wheel", "Enginee", "Glass"] 
```
Using keywork _arguments_ might be handy but we can mess up with the actual arguments if we have function with parameters.

For example

```javascript
var car = function(arg1, arg2, arg3) {
  arguments[1] = null;
  console.log("Arguments of this function are: ", arguments);
  console.log("First arg1: ", arg1);
  console.log("Second arg2: ", arg2);
  console.log("Third arg3: ", arg3);
};

car("Wheel","Enginee","Glass");
//Executing above code logs following output
Arguments of this function are:  ["Wheel", null, "Glass"]
First arg1:  Wheel
Second arg2:  null
Third arg3:  Glass
```
As we can see that changing keyword _arguments_ affected arg2 which is passed as a parameter(which is not modified anywhere). It might create trouble if arg2 is used below in the function. To solve this issue we can use following approach

```javascript
var car = function(arg1, arg2, arg3) {
  var args = Array.prototype.slice.call(arguments,0);
  args[1] = null ;
  console.log("Arguments of this function using arguments keyword: ", arguments);
  console.log("Arguments of this function are: ", args);
  console.log("First arg1: ", arg1);
  console.log("Second arg2: ", arg2);
  console.log("Third arg3: ", arg3);
};

car("Wheel","Enginee","Glass");
//Executing above code logs following output
Arguments of this function using arguments keyword:  ["Wheel", "Enginee", "Glass"]
Arguments of this function are:  ["Wheel", null, "Glass"]
First arg1:  Wheel
Second arg2:  Enginee
Third arg3:  Glass
```
