---
layout: post
title: Deadly sins of javascript implementation
subtitle: Javascript bad practices
bigimg: /img/js-sins.jpg
---

### Using global variabes, functions and DOM level-1 event handlers unappropriately
Global variables and function defined in one script can be overwritten by second script if it has same names.
This might cause unexpected results. Therefore, we should be careful while using global variables or functions or event handlers.  
- Things to remember 
  - Every script in a HTML document have same right as other scripts, therefore code snippet written in one script can  be overwritten by other script.
  - If you define global variables or function names and include other file using same names, than second file will overwrite the first implementation.
  - If you attach event on _onEvent_ DOM level-1 function and include another file which uses same event name, than second file will overwrite the first implementation.

Let's say you have script_one.js file with following code

```javascript
x = 4;
function init() {
  alert("init script one");
  document.getElementsByTagName('h1')[0].onclick = function() {
   this.style.background = 'blue';
  }
}
alert("The value of x in script one is "+ x);
window.onload = init;
```
Immediately after script_one.js, include script_two.js with following code block  

```javascript
x = 40;
function init() {
  alert("init script two");
  document.getElementsByTagName('h1')[0].onclick = function() {
   this.style.background = 'red';
  }
}
alert("The value of x in script two is "+ x);
window.onload = init;
```

