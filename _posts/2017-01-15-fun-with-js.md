---
layout: post
title: Fun with JavaScript
subtitle: Check your JS knowledge by answering the expected output?
---

### 1. What is the expected output of following code snippet?
```javascript
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```
```javascript
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 == 0.3);
```

```javascript
console.log(typeof NaN === "number");  // logs "true"
console.log(NaN === NaN);  // logs "false"
```

```javascript
(function() {
    console.log(1); 
    setTimeout(function(){console.log(2)}, 1000); 
    setTimeout(function(){console.log(3)}, 0); 
    console.log(4);
})();
```
