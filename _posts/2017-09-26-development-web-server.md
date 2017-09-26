---
layout: post
title:  "Setting up a development web server"
date:   2017-09-26 12:05:28 +0800
categories: dev-environment-setup configuration node-js
---

Using Express to run app locally
---

Express is a web server that is both easy to set up and configure to run locally, but robust enough to be able to use in production.

Setup simply by adding the package to your `package.json`

And configure in a javascript file - the below shows the basic (bare minimum?)

{% highlight JavaScript %}

import express from 'express';
import path from 'path';
import open from 'open';

const port = 3000;
const app = express();

app.listen(port, function(err){
	if(err){
		console.log(err);
	}
	else{
		open('http://localhost:'+port);
	}
});

{% endhighlight %}

Sensible to keep configuration scripts together in project - for example in a `root\buildScripts\` folder - this can hold the config files for everything needed to develop the app.


*Other options*

- http-server
- live-server (offering live reloading)

*Write up of notes from Pluralsight: Building a JavaScript Development Environment*