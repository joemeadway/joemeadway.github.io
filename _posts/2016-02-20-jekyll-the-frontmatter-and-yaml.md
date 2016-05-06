---
layout: post
title:  "Jekyll - the Front Matter, and YAML"
date:   2016-02-20 20:25:00 +0800
categories: jekyll yaml
---
The front matter is a block of YAML code that indicates to Jekyll that the file is special in some way. As a simple example, in the example index.html:
{% highlight yaml %}
---
layout: default
---
{% endhighlight %}
This is probably the most basic example possible, and (obviously) it indicates to Jekyll which layout to use when generating the index.html page. Simply put, between the dashes at the top of the file, one can put variables, both predefined (like 'layout') or custom (e.g. 'title'), which are then available to the Liquid templating engine that Jekyll uses. So, Liquid picks up 'layout' to use the relevant template; and could output 'title' like
{% highlight liquid %}{% raw %}
<h1>{{ site.title }}</h1>
{% endraw %}{% endhighlight %}


Predefined variables are:  
layout  
permalink - to define a url for a post, rather than the default year/month/day/title  
published - false indicates post should not be published when site is generated  
category/categories - can be used instead of folders to group posts  
tags  

**Default values**

You can set default values in the _config.yaml - for example, a default layout can be set for all posts with
{% highlight yaml %}
defaults:
    scope:
      path: "" #a blank path value indicates all files in the project
      values:
        layout: "default-layout"
{% endhighlight %}

So... YAML?

YAML Ain't Markup Language - "What It Is: YAML is a human friendly data seriliazation standard for all programming languages" (from [YAML.org][yaml-site])

So, YAML is a data format that is designed to be both serializable and human readable, but by design prioritizes the readability.

As a side note, I was going to have a parethetical "like JSON", but removed it. A little doubt had crept in, was I really *sure* JSON was a data format? I thought I was, but... I had some choric voice scoffing at yet another mistake this moron was making. So I looked it up quickly, and the calrification was quite interesting, and could probably work for a future post. In short, YAML is a superset of JSON - all valid JSON will be able to be parsed by a YAML parser. And JSON is a data format. Probably. 

Quite neatly, the yaml.org homepage is a completely valid YAML document, and could be parsed as such. It also demonstrates how readable the format is. 

And simply, YAML is the format used for the Front Matter in Jekyll. It could have been JSON, it could have been XML, it could have been... something else. If I was guessing, YAML would have been chosen as it is easy to read, fairly easy to write by hand, and probably quite popular in the Ruby community for those reasons, given the approach of the language to value the enjoyment of the programmer over other factors in the language design.

[yaml-site]: [http://yaml.org/]