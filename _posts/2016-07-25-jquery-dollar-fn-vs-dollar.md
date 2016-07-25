---
layout: post
title:  "jQuery plugins: using $.fn.pluginName vs. $.pluginName"
date:   2016-07-25 16:10:00+0800
categories: javascript jquery
---

In process of consolidating notes on writing jQuery plugings, and came across some confusion over scope when writing plugins. Some (like: <http://stefangabos.ro/jquery/jquery-plugin-boilerplate-oop/>) have the plugin declared as 

```
$.pluginName = function(el, options) { etc. }
```

while the majority (and the [documentation](https://learn.jquery.com/plugins/)) have it as 

```
$.fn.pluginName = function( options ) { etc. }
```

So what's the difference? Best explanation I've found is here: <http://stackoverflow.com/a/2845989>. In short, `$.fn.pluginName` extends the *prototype* of jQuery, while `$.pluginName` extends the jQuery *object itself*. Each will be called slightly differently:

```
$.pluginName($('#selection'), {} );
```

vs.

```
$('#selection').pluginName( {} );
```

And the explanation given is that the first is better used when you're not actually manipulating the DOM, and the latter when you are - the example of given on the SO answer is of a logging library, that won't actually affect the DOM elements at all, but log information about them. 

While I can see the worth in the first approach, it doesn't allow method chaining, and as such rather breaks jQuery's plugin model. Is this simply a case when you shouldn't use jQuery, but instead plain javascript? I'm still not certain of the benefits of the approach - the site linked above gives 'better performance and memory usage by not creating multiple instances of itself and attaching them to the target DOM elements', but I'll need to read more into that.
