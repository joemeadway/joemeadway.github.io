---
layout: post
title:  "Jekyll and Sass"
date:   2016-02-16 21:00:00 +0800
categories: jekyll sass
---

Uses .scss format by default

The main.scss file should go in the css folder. This file is the entry point for the stylesheets. Any partial sheets that are being imported should go in the _scss folder, but this can be edited with a line in the _config.yaml:
{% highlight yaml %}
sass:
     sass_dir: _other-location
{% endhighlight %}