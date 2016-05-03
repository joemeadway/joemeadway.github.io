---
layout: post
title:  "Jekyll _includes"
date:   2016-02-17 20:35:00 +0800
categories: jekyll 
---

The default example Jekyll site has an _include folder, containing short HTML snippet files such as header.html, footer.html and icon-twitter.html

In short, this folder allows us to define reusable snippets of HTML that we can drop into a page, thus reducing the amount of repeated code in our site. So, the icon-twitter.html contains a link to a twitter account, which is included in the footer.html partial.

The icon-twitter.html partial takes a parameter - the actual name of the twitter account is inserted by

{% highlight liquid %}{% raw %}
{% include.username %}
{% endraw %}{% endhighlight %}

But it's not initially clear where this username comes from - we can change it by changing the _config.yaml file, where we can see the 
{% highlight yaml %}
twitter_username: jekyllrb
{% endhighlight %}
line is set by default. But obviously this variable name doesn't match - so how does it get inserted?

It becomes clear if we trace where the icon-twitter.html file is referenced in the rest of the site. In footer.html (another partial in _includes), we find the line

{% highlight liquid %}{% raw %}
{% include icon-twitter.html username=site.twitter_username %}
{% endraw %}{% endhighlight %}

Two things of interest - 1) we name the parameter as we declare where the partial should be inserted; and 2) we pull the variable out of the _config.yaml using `site.twitter_username`.

Finally, the footer.html partial is included in the default.html template, found in the _layouts folder.
