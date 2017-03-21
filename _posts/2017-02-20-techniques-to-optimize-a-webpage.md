---
layout: post
title: What are several techniques to optimize webpages?
subtitle: Collection of techniques to optimize loading time of a webpage.
---

In this post I would like to mention about the techniques which can be applied to reduce the loading time of a webpage. There are 
several optimization techniques that can be used to boost up the performance any webapplication. If you know about other optimization techniques
other than the techniques listed below, please let me know through the comment section on the bottom of the page. I would love to know more about the 
optimization techniques.

### Generation of minified files
We can generate minified version of html, CSS and javascript files we have used in our application. There are several tools that can be used to generate minified version of the code use have used in our application such as grunt, gulp and soon.

### Lazy loading
Do not load unnecessary files which is not used in a particular web page. Based on the requirement of a web page, we should load only the required CSS or JavaScript files used by a webpage.

### Remove unused CSS codebase
Most of the time we use libraries like bootstrap to implement certain features but we do not use all the features provided by bootstrap. This can result in enormous amount of unused styles loaded unnecessarily on a webpage. Therefore, we can use tools like `uncss` to remove unused styles. [Uncss](https://github.com/giakki/uncss)
