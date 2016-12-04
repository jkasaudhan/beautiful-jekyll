---
layout: post
title: Deadly sins of javascript implementation
subtitle: Javascript bad practices
bigimg: /img/js-sins.jpg
---

### 1. Using global variabes, functions and DOM level-1 event handlers unappropriately
Global variables and function defined in one script can be overwritten by second script if it has same names.
This might cause unexpected results. Therefore, we should be careful while using global variables or functions or event handlers.  

  * Every script in a HTML document have same right as other scripts, therefore code snippet written in one script can  be overwritten by other script.
  * If you define global variables or function names and include other file using same names, than second file will overwrite the first implementation.
  * If you attach event on _onEvent_ DOM level-1 function and include another file which uses same event name, than second file will overwrite the first implementation.

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
If you execute these scripts in a browser, you will find that it alerts 4 and 40 and executes init script two but not script one. It means init function of script_two.js overwrites the first init and init function of script_one.js is never executed.

Background of the text becomes red if you click on the text but it never gets blue. [Demo](https://plnkr.co/edit/EWe7gjcPZkSJ4MkHabq2)

Solution to avoid this problem is to avoid using onEvent handlers.You can use proper DOM level-2 event handlers (it won't work in IE) as described below. Similarly, wrap your code with unique function names to avoid overriding from each other.

```javascript

var scriptOne = function() {
  var x = 5;
  function init() {
    alert('script one init');
    document.getElementsByTagName('h1')[0].addEventListener(
      'click',
      function(e) {
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

var scriptTwo = function() {
  var x = 10;
  function init() {
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

```javascript
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

### 2. Using wrong technology for the job
Most of the time we are habituated to hack our own code and get the things done. But this might lead to unmaintanable code which is hard for other future developers to work on. Therefore, its necessary to follow up some standards.

* Regardless of the environment it will be displayed in, only essential content and mark-up should be in HTML.
* Any sort of _Look And Feel_ elements should be controlled by CSS. Try to avoid changing color stuff using javascript.
* Any sort of interactions with the user beyond hover effects  should be done by javascript.

Let's take an example of how things can be done in a hacky and standard way. Let's say we have this HTML elements

```javascript
<h2>Section 1</h2>
<div class="section">
  <p>Section 1 content</p>
</div>

<h2>Section 2</h2>
<div class="section">
  <p>Section 2 content</p>
</div>

<h2>Section 3</h2>
<div class="section">
  <p>Section 3 content</p>
</div>

<h2>Section 4</h2>
<div class="section">
  <p>Section 4 content</p>
</div>
```
Now we want to open each section when its heading is clicked and highlight the content section. You can play around in [plunker](https://plnkr.co/edit/vGt2r9MNRGwii5Lg4VAv).
Normal jQuery solution to toggle the clicked section would be

```javascript
$(document).ready(function() {
  $('.section').hide();
  $('h2').click(function(e) {
    $(this).next().toggle();
  });
});
```

To highlight the content of the current section we normally prefer this way i.e controlling styling through javascript.

```javascript
$(document).ready(function(){
  $('.section').hide();
  $('h2').click(function(e){
    $(this).next().toggle();
    $(this).next().css('background','#ccc');
    $(this).next().css('border','1px solid #999');
    $(this).next().css('padding','5px');
  })
});
```
Few things are wrong with this apporach.

* For begineer we have made it hard to maintain the code by controlling look and feel through javascript but not CSS.
* Performance issue: eventhough jQuery is fast enough, there is a lot of code behind $('.section').hide().
* We have asked jQuery to find the next siblings four times and set the CSS. We can either set the value of $(this).next() in a variable and use it but we can avoid it by using map as below

```javascript
$(document).ready(function(){
  $('.section').hide();
  $('h2').click(function(e){
    $(this).next().toggle().css({
      'background':'#ffc',
      'border':'1px solid #999',
      'padding':'5px'
    });
  })
});
```
In this case we can open all the sections when heading for each section is clicked. What if we want to open only current section which is clicked. Normally, we would prefer following approach.
```javascript
$(document).ready(function(){
  $('.section').hide();
  $('h2').click(function(e){
    $('.section').hide();
    $(this).next().toggle().css({
      'background':'#ffc',
      'border':'1px solid #999',
      'padding':'5px'
    });
  })
});
```
This appraoch works fine but we are looping through the document lots of time whenever heading is clicked which is slow. Whenever $('.section').hide() is called after each click, jQuery goes through the document and applies the actions on the particular element which will create performance issue if it is called multiple times.








