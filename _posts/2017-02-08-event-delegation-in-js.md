---
layout: post
title: What is event delegation in JS?
subtitle: Do you know about event bubbling and capturing?
---

Before understanding event delegation let see what wikipedia says about `Delegation` "Delegation is the assignment of any responsibility or authority to another person". 
In the world of JS, event delegation means assigning responsibility of one element to another element. Let me explain it through an example.
Let's say we have a parent and child dom elements as shown below

```javascript
 <ul class="parent">
  <li class="child1"> child 1 </li>
  <li class="child2"> child 2 </li>
  <li class="child3"> child 3 </li>
  <li class="child4"> child 4 </li>
  <li class="child5"> child 5 </li>
 </ul>
```
