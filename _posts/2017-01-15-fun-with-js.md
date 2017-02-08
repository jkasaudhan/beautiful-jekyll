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

```javascript
for (var i = 0; i < 5; i++) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', function(){ console.log(i); });
  document.body.appendChild(btn);
}
```

```javascript
for (var i = 0; i < 5; i++) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', (function(i) {
    return function() { console.log(i); };
  })(i));
  document.body.appendChild(btn);
}
```

```javascript
['a', 'b', 'c', 'd', 'e'].forEach(function (value, i) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', function() { console.log(i); });
  document.body.appendChild(btn);
});
```

```javascript
for (var i = 0; i < 5; i++) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  (function (i) {
    btn.addEventListener('click', function() { console.log(i); });
  })(i);
  document.body.appendChild(btn);
}
```

```javascript
var arr1 = "john".split('');
var arr2 = arr1.reverse();
var arr3 = "jones".split('');
arr2.push(arr3);
console.log("array 1: length=" + arr1.length + " last=" + arr1.slice(-1));
console.log("array 2: length=" + arr2.length + " last=" + arr2.slice(-1));
```

```javascript
console.log(1 +  "2" + "2");
console.log(1 +  +"2" + "2");//+"2" returns 2 because unary operator + attempts to convert operand to number, if it is not already
console.log(1 +  -"1" + "2");
console.log(+"1" +  "1" + "2");
console.log( "A" - "B" + "2");
console.log( "A" - "B" + 2);
```
