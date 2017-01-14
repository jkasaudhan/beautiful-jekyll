---
layout: post
title: JavaScript context execution stack, functions and variable environments
subtitle: Do you know about scope chain?
---

### What is JavaScript execution context stack?
Whenever JS engine runs a piece of code, the environment in which it is executed is called execution context where variables and functions are actually resolved or executed.

Whenever a function is invoked, JS engine creates a new execution context and pushes it on top of the global execution context. Once a function finishes its execution, it is poped out from the stack. Let me explain it through an example.

Let's say we have following block of code and lets try to guess what would be the result.
```javascript
    function func2() {
      var meroVar;
      console.log(meroVar);
    }
  
    function func1() {
      var meroVar = 2;
      func2();
      console.log(meroVar);
    }
  
   var meroVar = 1;
   func1();
   console.log(meroVar);
```
It will print undefined , 2 and 1. So, whats actually happening here? 

![Execution Context Created By JS Engine](https://github.com/jkasaudhan/jkasaudhan.github.io/blob/master/img/ExecutionContext.png)

