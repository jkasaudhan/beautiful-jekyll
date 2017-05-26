---
layout: post
title: What are several techniques to optimize webpages?
subtitle: Collection of techniques to optimize loading time of a webpage.
---

In this post I would like to mention about the techniques which can be applied to reduce the loading time of a webpage. There are 
several optimization techniques that can be used to boost up the performance any webapplication. I have covered a brief introduction for each techniques rather than a detailed description. If you know about other optimization techniques
other than the techniques listed below, please let me know through the comment section on the bottom of the page. I would love to know more about the 
optimization techniques.

### Generation of minified files
We can generate minified version of html, CSS and javascript files we have used in our application. There are several tools that can be used to generate minified version of the code use have used in our application such as grunt, gulp and soon.

### Lazy loading
Do not load unnecessary files which is not used in a particular web page. Based on the requirement of a web page, we should load only the required CSS or JavaScript files used by a webpage.

### Remove unused CSS styles
Most of the time we use libraries like bootstrap to implement certain features but we do not use all the features provided by bootstrap. This can result in enormous amount of unused styles loaded unnecessarily on a webpage. Therefore, we can use tools like `uncss` to remove unused styles. [Uncss](https://github.com/giakki/uncss)

### Loading styles only for current viewport
Specially, in mobile devices we don't have to load all the styles required for a particular webpage rather we can load styles
for a portion of a page which is currently visible on the current viewport. This approach gives the feeling of smooth loading time without delay eventhough, it loads other styles slowly on the background.

### Browser caching
Whenever any webpage is loaded on the browser, we can cache CSS or images or JavaScript files so that we don't have to load it again and again when user is visiting next webpage. Do not forget to specify appropriate expiry date for the cacheable resources.

### Use proxy server
You can use proxy server to get the resources from intermediate server rather than the real server. Using nearby proxy server helps to reduce the response time and a webpage can load faster than it would load when it retrives resources from a real server.

### Server side rendering
There are several programming languages and tools that allows us to process html, evaluate expressions on server side. We can process html templates on server side and return the processed html content to the frontend so that browser just renders the dom elements along with its styles.

### Image Optimization
I have seen several high qulity images with resolution of 5000 * 5000 which is atleast 5 to 10 mb in size. We can use several tools to optimize the size of an image without degrading the quality of an image for different devices.

### Using preload and http2 push methods
We can download crucially important css or js files in a first request sent by browser to a server using preload method Eg. `<link rel='preload' href='css/main.css' as='style'>`. Watch these JSConf videos to understand how preload and push mechanism can help us optimize the performance of a webpage. [Browser hackers guide to load instantly everything](https://www.youtube.com/watch?v=7vUs5yOuv-o), [CSSconf EU 2017 | Patrick Hamann: CSS and the first meaningful paint](https://www.youtube.com/watch?v=4pQ2byAoIX0)


