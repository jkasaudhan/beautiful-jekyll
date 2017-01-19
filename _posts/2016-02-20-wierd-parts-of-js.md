---
layout: post
title: Weird parts of JavaScript?
subtitle: Collection of code snippets whose result looks unusual
---

Just to understand how JS works, I have been trying to make a list of JS code snippets whose output looks unusal to me. 
I am aware that, this is how JS works but it makes me feel weird about JS. Please let me know if you have figured out something like this, through the comment section below. It might be useful to debug our own code :)

### Data type of not a number is a number
When we try to get the type of NaN i.e not a number, it says typeof(NaN) is of number data type which is wierd in one way.

```javascript
  console.log(typeof(NaN)); //prints number
```

### Following behaviour is because of typeof(NaN) => number

```javascript
  console.log(angular.isNumber(parseInt('ee')));//prints true
```

### Type of null is an object

```javascript
  console.log(typeof(null)); //prints object
```

### Initially it feels wierd to see the output of the following code

```javascript
  function createFunctions() {
    var funcArray = [];
    for(var i=0; i< 4; i++) {
      funcArray.push(function() {
        console.log(i);
      });
  }
    return funcArray;
  }

  var funcList = createFunctions();
  funcList[0](); // prints 4
  funcList[1](); // prints 4
  funcList[2](); // prints 4
  funcList[3](); // prints 4
```
Eventhough we might expect it to print 0, 1, 2, 3 at first glance, it actually prints 4, 4, 4, 4. This is how JS works and is related to closure. I have separate post explaining how environment variables are executed in the execution context stack in this particular case.

### Looks wierd how 'this' object works ?

```javascript
function globalFunction() {
console.log(this);
}

//call global function
globalFunction(); //prints global Window object

var grandFather = {
  message: "I am your grand father.",
  //direct method inside an object grandFather 
  setMessage: function() {
      console.log("Inside grand father's setMessage: ", this.message);
      console.log("Inside setMessage of grandFather: ", this);

      var changeMessage = function() {
         //feels unsual to print global Window object in changeMessage method. Here, this object points to global Window object not      //grandFather object
          console.log("Inside inner method of grandFather i.e inside changeMessage: ", this);
      }

      changeMessage();
  },

  //creating new object father
  father: {
    message: "I am your father.",
    setMessage: function() {
        console.log("Inside father's setMessage: ", this.message);
        console.log("Inside father's setMessage: ", this);
    }

  }
}

grandFather.setMessage();
grandFather.father.setMessage();
```
Just wait for a minute and think what would be the result :). I have separate post on how 'this' object works.

Prints following result:-

Window {external: Object, chrome: Object, document: document, Prototype: Object, Class: Object…}

Inside grand father's setMessage:  I am your grand father.

Inside setMessage of grandFather:  Object {message: "I am your grand father.", father: Object}

Inside inner method of grandFather i.e inside changeMessage:  Window {external: Object, chrome: Object, document: document, Prototype: Object, Class: Object…} //feels unsual to print global Window object in changeMessage method. Here, 'this' object points to global Window object but not grandFather object

Inside father's setMessage:  I am your father.

Inside father's setMessage:  Object {message: "I am your father."}

### Invoke function before it is declared ?
Unlike other programming languages like C# or JAVA, it is not mandatory to declare or define functions before invoking it.

```javascript
  //function invokation before declaring it.
  printName(); 
  
  function printName() { 
    console.log("I am Jack Sparrow");
  }
```

We might expect it to throw an error because we are calling `printName()` function before its body is defined. But, it is not the case in JS. This is because of [Hoisting](/2016-12-08-js-execution-behaviour)
