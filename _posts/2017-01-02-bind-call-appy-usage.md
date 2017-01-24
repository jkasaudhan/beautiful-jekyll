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
  bindedPrintName();//prints Hi, I am  Jack Reacher
```

It is useful when we want to burrow functions from other object. Let's say we have a new object `user2` without `getFullName()` method. In this case we can burrow the function of `user` object to get the result. 

```javascript
  var user = {
    firstname: "Jack",
    lastname: "Reacher",
    getFullName: function() {
      //because 'this' object is used inside first level method of an object, it points to  user object
      return this.firstname + " " + this.lastname;
    }
  }
  
  var user2 = {
    firstname: "William",
    lastname: "Smith"
  }
  
  //.bind(user) does not invoke a function rather it returns a copy of getFullName method passing user2 object
  var bindedPrintName = user.getFullName.bind(user2);
  bindedPrintName();//prints William Smith
```

Similarly, we can use `.bind()` method for function currying, which means copying a function with some preset parameters.

```javascript
  function multiply(x, y) {
    return x * y;
  }
  
  //do not foucs on `this` object in this case, it is points to normal global Window object.
  //bind in this case accepts this object and first parameter value i.e x = 10
  var multiplyByTen = multiply.bind(this, 10);
  
   //bind in this case accepts this object and first parameter value i.e x = 6
  var multiplyBySix = multiply.bind(this, 6);
  
  console.log(multiplyByTen(2)); //prints 20
  console.log(multiplyBySix(5)); //prints 30 
```






