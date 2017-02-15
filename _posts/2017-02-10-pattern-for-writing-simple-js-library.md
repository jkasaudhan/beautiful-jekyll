---
layout: post
title: Pattern for writing simple JavaScript library? 
subtitle: How to write a simple JS library similar to jQuery?
---

I have been thinking about how jQuery works under the hood and how can I write something like jQuery. It looks like there
are standard patterns used by world class developers. I know there are several ways to write a library which encapsulates  variables and methods used inside the library. Here, I have wrote a simple Greet library used for displaying greet messages based on the supplied language. Similarly, we can learn about how to implement method chaining, expose methods outside the library, function prototypes etc.
Following code snippet allows us to use method chaining similar to `jQuery('ul li').addClass('class1').removeClass('class2');`

```javascript
var jk = $G("Jitendra", "Kasaudhan");
jk.greet().setLang('np').greet(true);// prints: Hi! Jitendra and Namaste Jitendra Kasaudhan
```


```javascript
(function(global) {
    //We have used immediately invoked function expression and supplied window as a global object
    if(!global) {
        throw "Global Window object is not available.";
    }
    var Greeter = function(firstname, lastname, lang) {
        return new Greeter.init(firstname, lastname, lang);
    }
    
    //Support English and Nepali language
    var supportedLang = ['en','np'];
    
    var formalGreetings = {
        'en': 'Dear',
        'np': 'Namaste'
    };
    
    var informalGreetings = {
        'en': 'Hi!',
        'np': 'K6?'
    }
    
    //Create a new init function constructor and return it when Greeter method is called.
    //It is also a pattern used in jQuery
    Greeter.init = function(firstname, lastname, lang) {
        var self = this;
        self.firstname = firstname || '';
        self.lastname = lastname || '';
        self.language = lang || 'en';
    }
    
    //Attach all the properties you want to expose out from this library to the users.
    Greeter.prototype = {
        getFromalGreetings: function() {
            return formalGreetings[this.language] + " " + this.firstname + " " + this.lastname;
        },
        getInformalGreetings: function() {
            return informalGreetings[this.language] + " " + this.firstname;
        },
        greet: function(isFormal) {
            if(isFormal) {
                //if greet is formal log formal output
                console.log(this.getFromalGreetings());
            }else {
                console.log(this.getInformalGreetings());
            }    
            
            //Returning 'this' Greet object will allow us to chain the methods. This is also a pattern used in jQuery.
            //It allows us to do var g = $G('jiten', 'kasaudhan'); g.greet().setLang('np');
            return this;
        },
        validateLangSupport: function(lang) {
            //Validate if language is supported or not
            if(supportedLang.indexOf(lang) === -1) {
                //if lang is not present in supportedLang throw error
                throw "Language not supported";
            }else {
                return true;
            }
        },
        setLang: function(lang) {
            this.validateLangSupport(lang);
            this.language = lang;
            
            //Returning this object returns Greet object which allows method chaining
            return this;
        }
    };
    
    //When var out = G$(...); is used outside this librarary, out.prototype should be able to access all the properties of Greeter.
    //Therefore Greeter.init() function constructor's prototype should point to Greeter prototype.
    Greeter.init.prototype = Greeter.prototype;
    
    //Creating alias so that user can call using Greeter(...) or $G(...)
    global.Greeter = global.$G = Greeter;
}(window));
```
