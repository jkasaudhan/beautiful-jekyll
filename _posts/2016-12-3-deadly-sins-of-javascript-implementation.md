---
layout: post
title: Deadly sins of javascript implementation
subtitle: Javascript bad practices
bigimg: /img/js-sins.jpg
---

## Using global variabes, functions and DOM level-1 event handlers unappropriately
Global variables and function defined in one script can be overritten by second script if it has same names.
This might cause unexpected results.
