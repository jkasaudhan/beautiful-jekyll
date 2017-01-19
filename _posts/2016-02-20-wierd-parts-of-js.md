---
layout: post
title: Wierd parts of JavaScript?
subtitle: Collection of code snippets whose result looks unusual
---

Just to understand how JS works, I have been trying to make a list of JS code snippets whose output looks unusal to me. 
I am aware that, this is how JS works but it makes me feel wierd about JS. Please let me know if you have figured out something like this, through the comment section below. It might be useful to debug our own code :)

### Type of not a number is a number
When we try to get the type of NaN i.e not a number, it says typeof(NaN) is of number data type which is wierd in one way.

```javascript
  console.log(typeof(NaN)); //prints number
```
### This is because of typeof(NaN) => number

```javascript
  console.log(angular.isNumber(parseInt('ee')));//prints true
```

### Type of null is an object

```javascript
  console.log(typeof(null)); //prints object
```

### Initially it feels wierd to see the output of the following code

```javascript
  function createFunctions() {
  var funcArray = [];

  for(var i=0; i< 4; i++) {

    funcArray.push(function() {
      console.log(i);
    });

  }

  return funcArray;
  }

  var funcList = createFunctions();

  funcList[0](); // prints 4
  funcList[1](); // prints 4
  funcList[2](); // prints 4
  funcList[3](); // prints 4
```
Eventhough we might expect it to print 0, 1, 2, 3 at first glance, it actually prints 4, 4, 4, 4. This is how JS works and is related to closure. I have separate post explaining how environment vaiables are executed in execution context in this particular case.
