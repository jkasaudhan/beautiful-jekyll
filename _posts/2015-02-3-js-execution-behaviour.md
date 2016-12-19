---
layout: post
title: Code execution beaviour in JS, every JS developer should know.
subtitle: Do you know about Hoisting?
bigimg: /img/matrix.jpg
---

Whenever we declare var x = 5, we might think it as one statement but the JavaScript enginee does not see it this way. It sees var x and x = 5 as two different statements which is explained in detail below which an example. Eventhough interpreter interprets the code line by line, it compiles the code before interpreting. Therefore, the first one var x, is compiler-phase task and the second one x = 5 is execution-phase task. All the declarations in a scope regardless of where they appear in the code are processed first before their execution i.e we can say that variables and function declarations are moved to the top of their respective scopes which is also called hoisting. Only declarations themselves are hoisted but not the assignments of functions or variables.

Most of the developers might think that JS programs are interpreted line-by-line from top to bottom as defined the program. But this is partially true.

```javascript
  x = 5;
  var x;
  console.log(x);
```
What do you expect? Most of us might think it will print undefined because `var x` is defined after `x = 5` so x must be re-declared whose value is undefined. However, it prints 5. Similarly, lets take another example

```javascript
  console.log(x);
  var x = 5;
```
What do you expect now? Most of us might think it will print 5 based on the explaination before but that's not true. Its undefined in this case and the reason for this is related with hoisting.

As I have mentioned before, JS enginee compiles our code before interpreting it. Therefore, during compilation phase, it finds and associates all the declations with their scopes i.e all the variable and function declarations are processed first before executing any piece of the code. JS enginee compiles and executes above code in the following way

```javascript
  var x;
```
This is done during compilation phase and during execution phase it executes as below

```javascript 
  x = 5;
  console.log(x); //prints 5
```
For the second code snippet, it executes in following order.

```javascript
  var x;
```
which is compilation phase.

```javascript
  console.log(x);//since x is not assigned with some value before printing it, its value is undefined
  x = 5;
```
For understanding details how it wokrs with function please visit this page
https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch4.md
