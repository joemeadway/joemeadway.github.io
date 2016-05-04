---
layout: post
title:  "Jekyll _layouts"
date:   2016-02-18 21:24:28 +0800
categories: jekyll
---
The _layouts folder contains HTML snippet files that define templates for laying out pages.

So, for example, the default.html layout lays out an HTML page, doctype declared at the top, then 
{% highlight html %}
<!DOCTYPE html>
<html>
{% raw %} 
  {% include head.html %}{% endraw %}

  <body>
{% raw %} 
    {% include header.html %}{% endraw %}

    <div class="page-content">
      <div class="wrapper">
        {% raw %} {{ content }} {% endraw %}
      </div>
    </div>

    {% raw %} {% include footer.html %} {% endraw %}

  </body>

</html>
{% endhighlight %}

the {% raw %} {% include %} {% endraw %} tags we've seen previously, and here we have the additional of {% raw %}{{ content }}{% endraw %} - we're grabbing a variable and inserting it. And this content variable is used on every layout snippet. It simply inserts the content from the .md file that uses the template.

How is the post linked to the layout? In the yaml at the top of the post file:

{% highlight yaml %}
layout: default
{% endhighlight %}

or rather more commonly with this blog:

{% highlight yaml %}
layout: post
{% endhighlight %}
