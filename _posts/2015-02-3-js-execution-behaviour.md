---
layout: post
title: Code execution beaviour in JS, every JS developer should know.
subtitle: Do you know about Hoisting?
bigimg: /img/matrix.jpg
---

Whenever we declare var x = 5, we might think it as one statement but the JavaScript enginee does not see it this way. It sees var x and x = 5 as two different statements which is explained in detail below which an example. Eventhough interpreter interprets the code line by line, it compiles the code before interpreting. Therefore, the first one var x, is compiler-phase task and the second one x = 5 is execution-phase task. All the declarations in a scope regardless of where they appear in the code are processed first before their execution i.e we can say that variables and function declarations are moved to the top of their respective scopes which is also called hoisting. Only declarations themselves are hoisted but not the assignments of functions or variables.

