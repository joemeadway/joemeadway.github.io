---
layout: post
title:  "Pluralsight: Getting started with Node - Accessing the Local System"
date:   2017-11-30 11:47:00 +0800
categories: node-js getting-started pluralsight
---

Series of object that expose certain processes and functions for the underlying OS.

Process
---

Info about the process the code is currently running in, and other processes on the System
Steam, info, attributes, process methods
Event emitter - exit(), uncaught exception

e.g. stdout, stdin, stderr

`process.stdin.on('data', function(chunk){...});`

stdin starts paused

- need to call resume() to be able to receive data

Interacting with Filesystem
---

Wrappers around POSIX functions, bot async and sync. e.g. rename, mkdir, etc.

Stream functions

`fs.createReadStream()`

- return an `fs.ReadStream`

`fs.createWriteStream();`

- returns a `fs.WriteStream`

Watch a file for changes

`fs.watch` --> returns an `fs.FileWatcher`

- event emitter - change, error

What is a buffer?
---

Javascript has difficulty dealing with binary data - Buffer class in a raw memory allocation for binary data.

Supports multiple encodings.

OS Module
---

Info about currently runnign System

`os.type()`
`os.release()`

And, useful

`os.EOL`

to get the native End of Line marker.

*Write up of notes from Pluralsight: Introduction to Node.js by Paul O'Fallon*