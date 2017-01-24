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
  
  
  
```
