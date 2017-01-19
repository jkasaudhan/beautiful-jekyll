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
