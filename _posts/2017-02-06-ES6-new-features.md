---
layout: post
title: What's new in ECMAScript6 (ES6)?
subtitle: Comparision between ES5 and ES6 features.
---

This post contains important new features introduced in ES6. We will go through the syntax used in ES5 side by side with ES6.

#### Classes

#### Modules

#### const and let 

#### Arrows functions
```javascript
//ES5 Style
var persons = [
  {name: 'Jack', age: 20},
  {name: 'Anthony', age: 20},
  {name: 'David', age: 25},
  {name: 'Hailer', age: 28},
  {name: 'Luke', age: 25}
];

var age20Persons = persons.filter(function(person) {
  return person.age === 20;
});
console.table(age20Persons);
//ES6 Style
var fullName = `${firstname} ${lastname}`;
```

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

#### Template Literals

```javascript
//ES5 Style
var fullName = firstname + ' ' + lastname;

//ES6 Style
var fullName = `${firstname} ${lastname}`;
```

#### Destructuring Assignment

```javascript
//ES5 Style
var data = jQuery('body').data();
//If jQuery('body').data() returns properties userName and email, we have to destructure in following way
var userName = data.userName;
var email = data.email;

//ES6 Style
var {userName, email} = jQuery('body').data();

//This is also valid for array
var [w1, w2, w3] = "word1, word2, word3".split(',');
```
