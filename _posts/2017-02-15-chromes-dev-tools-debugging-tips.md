---
layout: post
title: Debugging tips using chrome's developer's tool.
subtitle: Power of 'console' object?
---

If you have worked with JavaScript, probably you might be familiar with `console` object used for debugging. Most of the developers
are familiar with `console.log()`, `console,error()`, `console.info()` and `console.warn()`. There are other interesting stuff we can
do with `console` object which are listed below.

### 1) Embed styles
You can embed css styles while logging any text using %c as shown below. Try to copy and paste the console.log statement below in your developers tool and see the result. Isn't it cool?

```javascript
   console.log('%c This is cool', 'font-size: 20px; background-color: yellow; border: 5px solid red;');
```

### 2) Log in tabluar format
You can log your values in tablular format using `console.table()`

```javascript
  var users = [{name: "Jackie Chain", age: 40},{name: "Jack Sparrow", age: 30},{name: "Tom Hanks", age: 40}];
  console.table(users);
```
### 3) Log dom element and its directory
We can log the dom tree structure for any dom element using `console.dir()`.

```javascript
   var domElement = document.querySelector('p');
   console.log(domElement); //prints <p>..........</p>
   console.dir(domElement); // prints p with all the attributes in it.
```

### 4) Group logs under proper topic name
You can group console logs under proper topic name using `console.group(...)` and `console.groupEnd()`

```javascript

```
