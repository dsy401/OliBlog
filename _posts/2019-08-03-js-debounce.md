---
layout: post_layout
title: JS Debounce
time: 2019-08-03 Saturday
location: Auckland
pulished: true
excerpt_separator: '```'
---

These days, i have created a scheduler for my school management system project, i have met the problem that evert time i click the next button to turn to next page, so the frontend will send AJAX request for every i clicked, which will course server overloading. So, i thought of the debounce to avoid this happen.

There is the debounce source code written by myself

~~~javascript
const debounce = () => {
    let timeout = null; //timeout: null
    if (timeout){ //if timeout is not null
        clearTimeout(timeout) //clear timeout to null
    }
    return (fn,delay) => {
        timeout = setTimeout(()=>{
            fn()
        }, delay)
    }
}
~~~

How to use it?

~~~javascript
const method = debounce()
method(()=>{
    //your work
}, 500) //your custom delay microseconds
~~~

When i use the debounce, each time i click the button to turn to the next pgae, the system will not Immediately send the AJAX request to server. The AJAX request will be sent After the click action stops for your custom delay (microseconds).