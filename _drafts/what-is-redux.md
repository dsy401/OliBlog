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

&nbsp;

#### Design thinking

1. A web application is a state machine, and the view and state are one-to-one.
2. All states are saved in an object.

#### Store

&nbsp;

Store is the place to save data, you can think of it as a container, an application can only have one redux.

&nbsp;

Redux provides the createStore function to generate the Store:

&nbsp;