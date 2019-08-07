---
layout: post_layout
title: React Component Lifecyle
date: 2019-06-06 06:24:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

&nbsp;

In this chapter we will discuss the life cycle of React components. The life cycle of a component can be divided into three states: Mounting (inserted real DOM), Updating (re-rendering) and Unmounting (removed real DOM).

The life cycle methods are:

1. ***componentWillMount*\:&nbsp;**Called before rendering, on the client side also on the server side.
2. ***componentDidMount***&nbsp;: Called after the first render, only on the client side. The component has then generated the corresponding DOM structure, which can be accessed via this.getDOMNode(). If you want to work with other JavaScript frameworks, you can call setTimeout, setInterval or send an AJAX request in this method (to prevent asynchronous operations from blocking the UI).
3. ***componentWillReceiveProps*****\:&nbsp;**Called when the component receives a new prop (updated). This method will not be called when the render is initialized.
4. ***shouldComponentUpdate*\:&nbsp;**Returns a boolean value. Called when the component receives a new props or state. Not called at initialization or when using forceUpdate.
5. ***componentWillUpdate*\:&nbsp;**Called when the component receives a new props or state but has not yet rendered. It will not be called during initialization.
6. ***componentDidUpdate*\:&nbsp;**Called immediately after the component has completed the update. It will not be called during initialization.
7. **componentWillUnmount:&nbsp;**Called immediately before the component is removed from the DOM.