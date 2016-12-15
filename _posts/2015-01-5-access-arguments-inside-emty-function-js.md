---
layout: post
title: How to access arguments inside an empty function in JS?
subtitle: Importance of keywork _arguments_
bigimg: /img/path.jpg
---

### 1.How to access arguments inside an empty function in JS? 
Eventhough the function declared is an empty function, we can pass the arguments to that function and access those arguments inside
an empty function, simply by using keyword _arguments_.

For example

```javascript
var car = function() {
  console.log("Arguments of this function are: ", arguments);
};

car("wheel","enginee","Glass");
//Executing above line will log: ["wheel", "enginee", "Glass"] 
```
