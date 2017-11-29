---
layout: post
title:  "Pluralsight: Getting started with Node - Introduction"
date:   2017-11-29 14:27:00 +0800
categories: configuration node-js getting-started pluralsight
---

Node is built from   

- **libuv** a cross-platform event I/O library
- **v8** Google's javascript engine

Written in C++ and javascript.

Node's event loop
---

In browser, we are always listening for DOM events. Node carries this idea over to server-side runtime.

Node has same concept

- listening for events    
    - http
    - timers
    - requests to external resources, and responses
- all events are handled discretely
- non-blocking

Node conventions
---

Functions passed as parameters - callbacks and event emitters

- Callback is always last parameters
- Error is passed as first parameter - and check if error is undefined
- Closures are your friend

But, avoid too many nested anonymous functions - look to use streams or named functions to provide clarity. 




*Write up of notes from Pluralsight: Introduction to Node.js by Paul O'Fallon*