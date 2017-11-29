---
layout: post
title:  "Pluralsight: Getting started with Node - Events and Streams"
date:   2017-11-29 16:58:00 +0800
categories: configuration node-js getting-started pluralsight
---

Callbacks are typically used to implement asynchronous, non-blocking code (though can also use events)

**Callback**


```
getThing(params, function(err, params){

});
```

**Event**

```
var results = getThing(params);
results.on('event', function(param){
    //do something with params
});
```

Here, results is an `EventEmitter` class.

- publish/subscribe
- handle results as they arrive
- get partial results before error

Event Emitter
---
Publisher --> Subscriber

`emitter.emit(event, [args]) --> emitter.on(event, listener)`

- event can be any string, with zero or more arguments

Common pattern for EventEmitters

- retrn valuie from a function call
- objects that extend EventEmitter to emit events themselves

Streams
---
Streams extend EventEmitter with an interface

- an abstraction for managing data flow - e.g. Network traddic, File I/O
- Stream is readable, writable, or both.
- Content can be piped from readable, to writable.

**Readable Streams Interface**

- boolean [readable]
- events - data, end, error, close
- methods - pause, resume, destroy, pipe

**Writable stream interface**

- boolean [writeable]
- events - error, drain, close, pipe
- methods - write, end

(not exhaustive)

Pipe() - pass in writable destination

e.g. request - readable http stream

```
var s = request('url);

//s is a stream
//so can subscribe

s.on('data', ...)

```


*Write up of notes from Pluralsight: Introduction to Node.js by Paul O'Fallon*