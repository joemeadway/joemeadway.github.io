---
layout: post
title:  "Pluralsight: Getting started with Node - Interacting with The Web"
date:   2017-11-30 11:47:00 +0800
categories: node-js getting-started pluralsight
---

Client, server, and using sockets

Making Requests
---

`var http = require('http')'`

request function - takes, options, and callback

returns request object, a writable stream

Also have `http.get()` for simple GET Requests

As a Server
---

```
var server - http.createServer(function(req, response){});
server.listen(port, host);
```

req - can be read or piped elsewhere
response - writable response

`https.createServer();` for SSL

Real Time with Socket.IO
---

Starts, and then uses event emitter, and an equivalent listener on the Client

Symmetry of client and server, both can emit and listen for each other's events


*Write up of notes from Pluralsight: Introduction to Node.js by Paul O'Fallon*