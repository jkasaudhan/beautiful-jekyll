---
layout: post
title: Debugging tips using chrome's developer's tool.
subtitle: Power of 'console' object?
---

If you have worked with JavaScript, probably you must be familiar with `console` object used for debugging. Most of the us are familiar with `console.log()`, `console,error()`, `console.info()` and `console.warn()` but there are other interesting stuff we can do with `console` object which are listed below.

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
You can log the dom tree structure for any dom element using `console.dir()`.

```javascript
   var domElement = document.querySelector('p');
   console.log(domElement); //prints <p>..........</p>
   console.dir(domElement); // prints p with all the attributes in it.
```

### 4) Group logs under proper topic name
You can group console logs under proper topic name using `console.group(...)` and `console.groupEnd()`

```javascript
//log user related logs in a group
console.group('users logs'); 
   console.log('Name: ', 'jk');
   console.log('Age: ', '30'); 
   console.log('Email: ', 'jk@jk.com');
console.groupEnd('users logs');

//log product related logs in a group
console.group('products logs'); 
   console.log('Name: ', 'Mobile');
   console.log('Cost: ', '400EUR'); 
   console.log('Model: ', 'Nexus');
console.groupEnd('products logs');

//logs product related logs in a group but in collapse format
console.groupCollapsed('products logs'); 
   console.log('Name: ', 'Mobile');
   console.log('Cost: ', '400EUR'); 
   console.log('Model: ', 'Nexus');
console.groupEnd('products logs');
```

### 5) Log only if certain condition is false
You can use `console.assert()` to check if certain value is true or false and log only if the condition is false.

```javascript
  //if condition is true it wont logs the statement 
  console.assert(1 === 2, "Logs only if condition is false");
```

### 6) Count log terms
You can count the terms used for loggin using `console.count()`

```javascript
   console.count('Hello'); //prints Hello: 1
   console.count('Hello'); //prints Hello: 2
   console.count('Hello'); //prints Hello: 3
   console.count('Hello'); //prints Hello: 4
```

You can find more about deugging techniques here [1](https://developers.google.com/web/tools/chrome-devtools/console/)
[2](http://blog.teamtreehouse.com/mastering-developer-tools-console)
