---
layout: post
title: What's new in ECMAScript6 (ES6)?
subtitle: Comparision between ES5 and ES6 features.
---

This post contains important new features introduced in ES6. We will go through the syntax used in ES5 side by side with ES6.

#### Classes

```javascript
//ES5 Style
var Shape = function(id, dx, dy) {
    this.id = id;
    this.move(dx, dy);
}

Shape.prototype.move = function(dx, dy) {
    this.x = dx;
    this.y = dy;
}

var shape = new Shape(1, 5, 10);
console.log(shape);

//ES6 Style
class Shape {
  constructor(id, dx, dy) {
    this.id = id;
    this.move(dx, dy);
  }
  
  move(dx, dy) {
    this.dx = dx;
    this.dy = dy;
  }
}

var shapeES6 = new Shape(2, 20, 30);
console.log(shapeES6);
```

#### Modules
We can export functions or objects or variables in one file and import into another file without any global namespace conflicts.

```javasctipt
//ES5 Style
//  lib/math.js
LibMath = {};
LibMath.sum = function (x, y) { return x + y };
LibMath.pi = 3.141593;

//  someApp.js
var math = LibMath;
console.log("2π = " + math.sum(math.pi, math.pi));

//  otherApp.js
var sum = LibMath.sum, pi = LibMath.pi;
console.log("2π = " + sum(pi, pi));


//ES6 Style
//  lib/math.js
export function sum (x, y) { return x + y }
export var pi = 3.141593

//  someApp.js
import * as math from "lib/math"
console.log("2π = " + math.sum(math.pi, math.pi))

//  otherApp.js
import { sum, pi } from "lib/math"
console.log("2π = " + sum(pi, pi))
```
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

//Filters array, can change the size of an array after filter is applied.
var age20Persons = persons.filter(function(person) {
  return person.age === 20;
});
console.table(age20Persons);

//Modifies the value of an array item but map does not change the size of an array.
var presonGreetings = persons.map(function(person) {
  return "Hello, " + person.name;
});
console.log(presonGreetings);

//ES6 Style, using arrow notation
//Filters array, can change the size of an array after filter is applied.
//We can just pass parameters instead of using function(data){} and direclty return value without usind return statement.
var age20Personses6 = persons.filter(person => person.age === 20);
console.table(age20Personses6);

//Modifies the value of an array item but map does not change the size of an array.
var presonGreetingses6 = persons.map(person =>  "Hello, " + person.name);
console.log(presonGreetingses6);

//If we have multiple parameters to a function and a block of code to execute we can use following syntax
var getResults = (persons, increament) => {
  console.log("Age increased by: ", increament);
  return persons.map(per => per.age*increament);
};
console.log(getResults(persons, 2));
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
[Reference 1](https://webapplog.com/es6/)
[Reference 2](http://es6-features.org/#ClassDefinition)
[Reference 3](https://github.com/lukehoban/es6features)
