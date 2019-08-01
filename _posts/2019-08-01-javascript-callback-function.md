---
layout: post_layout
title: JavaScript Callback Function
time:
location: Auckland
pulished: true
excerpt_separator: '```'
---

Here are a few concepts introduced firstly.

### **Function is also an object **

To understand the callback function, first understand the rules of the function clearly. In javascript, the function is strange, but it is really an object. Specifically, a function is a Function object created with the Function() constructor. The function object contains a string containing the javascript code of the function. If you are transferring from C or Java, this may seem strange, how can the code be a string? But for javascript, this is very common. The difference between data and code is very vague.

~~~javascript
var fn = new Function("arg1", "arg2", "return arg1 * arg2;");
fn(3, 7); // return 3*7=21
~~~

One benefit of this is that you can pass code to other functions, or you can pass regular variables or objects (because the code is literally just an object).

### Deliver function as callback

~~~javascript
function fn(arg1, arg2, callback){
 var num = Math.ceil(Math.random() * (arg1 - arg2) + arg2);
 callback(num);　　//deliver result
}
 fn(10, 20, function(num){
 console.log("Callback called! Num: " + num); 　//result will be random number betwwen 10 and 20
});
~~~

Maybe it seems cumbersome to do this, even stupid, why not return the results normally? But when you have to use a callback function, you probably don't think so\! Don't block, traditional functions enter data as parameters and return values ​​using a return statement. In theory, there is a return return statement at the end of the function, which is structurally: an input point and an output point. It's easier to understand that a function is essentially a mapping of the implementation process between input and output. However, when the implementation of the function is very long, do you choose to wait for the function to complete the processing, or use the callback function for asynchronous processing? In this case, it is important to use a callback function, such as an AJAX request. If you use the callback function for processing, the code can continue with other tasks without having to wait. In actual development, asynchronous calls are often used in javascript, and it is highly recommended here\!