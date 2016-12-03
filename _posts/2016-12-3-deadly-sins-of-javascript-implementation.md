---
layout: post
title: Deadly sins of javascript implementation
subtitle: Javascript bad practices
bigimg: /img/js-sins.jpg
---

### Using global variabes, functions and DOM level-1 event handlers unappropriately
Global variables and function defined in one script can be overwritten by second script if it has same names.
This might cause unexpected results. Therefore, we should be careful while using global variables or functions or event handlers.  


Let's say you have script_one.js file with following code

```
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
```
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
If you execute these scripts in a browser, you will find that it alerts 4 and 40 and executes init script two but not script one. It means init function of script_two.js overwrites the first init and init function of script_one.js is never executed.
Background of the text becomes red if you click on the text but it never gets blue. [Demo](https://plnkr.co/edit/EWe7gjcPZkSJ4MkHabq2)

Solution to avoid this problem is to avoid using onEvent handlers.You can use proper DOM level-2 event handlers (it won't work in IE) as described below. Similarly, wrap your code with unique function names to avoid overriding from each other.

```
var scriptOne = function(){
  var x = 5;
  function init(){
    alert('script one init');
    document.getElementsByTagName('h1')[0].addEventListener(
      'click',
      function(e){
        var t = e.target;
        t.style.background = 'blue';
      },
      false
    );
  }
  alert('x inside is '+x);
  return {init:init};
}();
window.addEventListener('load',scriptOne.init,false);
alert('x outside is '+x);

var scriptTwo = function(){
  var x = 10;
  function init(){
    alert('script two init');
    document.getElementsByTagName('h1')[0].addEventListener(
      'click',
      function(e){
        var t = e.target;
        t.style.color = 'white';
      },
      false
    );
  }
  alert('x inside is '+x);
  return {init:init};
}();
window.addEventListener('load',scriptTwo.init,false);
alert('x outside is '+x);
```
In this way everything executes as expected, x inside is 5 and than 10 and text changes to blue when you click on the text.
By moving x inside a function and using keyword _var_ infront of them, we have made them visible within those functions and restricted outside world to use that variable directly. This is called _Closure_ which is the powerful feature of javascript.

[Module Pattern](http://www.christianheilmann.com/2007/07/24/show-love-to-the-module-pattern/) is considered as the best practices while creating closure function that retruns function which should be acceble to the outside world.
```
var scriptOne = function() {
  var x = 4;
  var f = 3;
  function load(){}
  function init(){}
  return {
    init:init
  } 
}();
```
In this way, we can access load and init function by scriptOne.load() or scriptOne.init(). This technique will safeguard all your variables and functions. 
