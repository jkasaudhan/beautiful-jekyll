---
layout: post
title: When should we use .bind(), .call() and .apply() methods ?
subtitle: Usage of bind, call and apply methods
tags: [.bind(), .call(), .apply(), JS]
---

It is necessary to understand how .bind(), .call() and .apply() method works before finding the use cases to apply these methods. As we know, functions in JS are special type of objects and it contains .bind(), .call() and .apply() methods by default, serving special purpose. Let me explain it through an example

### .bind() method

```javascript
  var user = {
    firstname: "Jack",
    lastname: "Reacher",
    getFullName: function() {
      //because 'this' object is used inside first level method of an object, it points to  user object
      return this.firstname + " " + this.lastname;
    }
  }
  
  //function to print name of the user
  var printName = function() {
    //in this case 'this' object will point to global Window object
    console.log("Hi, I am ", this.getFullName());
  }
  
  printName();//shows an error Uncaught TypeError: this.getFullName is not a function
```

Trying to invoke `printName()` propmts an error because `this` object points to gobal Window object which does not have function `getFullName()`. In this situation, what if we can control `this` object to point to user object? JS allows us to control `this` object inside `printName()` method using `.bind()` method.

```javascript
  var user = {
    firstname: "Jack",
    lastname: "Reacher",
    getFullName: function() {
      //because 'this' object is used inside first level method of an object, it points to  user object
      return this.firstname + " " + this.lastname;
    }
  }
  
  //function to print name of the user
  var printName = function() {
    //in this case 'this' object will point to global Window object
    console.log("Hi, I am ", this.getFullName());
  }
  
  //.bind(user) does not invoke a function rather it returns a copy of printName method passing user object
  var bindedPrintName = printName.bind(user);
  bindedPrintName();
```
