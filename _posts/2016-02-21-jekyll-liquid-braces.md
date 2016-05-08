---
layout: post
title:  "Jekyll - Liquid using double braces vs. brace-percentage"
date:   2016-02-21 21:36:00 +0800
categories: jekyll liquid
---

What's the difference between {% raw %}{{ }}{% endraw %} and {% raw %}{% %}{% endraw %} ?

Taking a look in the default.html layout, we can see both used.

{% highlight liquid %}{% raw %}{{ content }}{% endraw %}{% endhighlight %}

is just referencing a variable, 'content', which will be output directly onto the page. In contrast

{% highlight liquid %}{% raw %}{% include head.html %}{% endraw %}{% endhighlight %}

Is using a keyword, include, and won't be directly output - rather, the result of the call to 'include' will be output, and it so happens that 'include' renders a partial. These can also be used to implement logical conditions for rendering different elements, for example, whether to render a twitter username or not depending whether it is defined in the site _config.yaml
{% highlight liquid %}{% raw %}
{% if site.twitter_username %}
<li>
{% include icon-twitter.html username=site.twitter_username %}
</li>
{% endif %}
{% endraw %}{% endhighlight %}
Equivalents in ASP.NET, for example, using the Razor syntax  

```  
@if (foo){  
     [elements to render] or  
     @model.SomeProperty  
}  
```  

or even  

```  
<% if (foo) { %>  
     [Elements to render] or  
     <%= model.SomeProperty %>  
<% } %>  
```  

(Just a little reminder how horrible the Web Forms syntax is...)
