---
layout: post_layout
title: What is Redux
date: 2019-06-20 23:01:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

### What is VM of MVVM?

The VM is responsible for synchronizing the Model data to the View display, and is also responsible for modifying the View's modifications back to the Model.

### **Redux**

#### Design thinking

1. A web application is a state machine, and the view and state are one-to-one.
2. All states are saved in an object.

#### Store

Store is the place to save data, you can think of it as a container, an application can only have one redux.

Redux provides the createStore function to generate the Store:

~~~javascript
import { createStore } from 'redux';
const store=createStore(fn);
~~~

1\. When we need to modify the state, we need to dispatch an action

~~~javascript
store.dispatch(action);
~~~

2\.store needs to make the corresponding changes to receive the action. Called reducer, the reducer is passed in as a parameter in createStore

~~~javascript
const defaultState = 0;
const reducer=(state=defaultState,action)=>{
    switch(action.type){
        case 'ADD_TO':
        return state+action.payload;
        default:state;
    }
}
const store=createStore(reducer);
~~~

3\. After the state is changed, the view needs to be updated automatically. Use store.suscribe(listener) to listen. Automatic update if you write render or getState to listener