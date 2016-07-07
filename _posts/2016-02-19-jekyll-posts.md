---
layout: post
title:  "Jekyll _posts"
date:   2016-02-19 22:00:00 +0800
categories: jekyll
---
'Posts' covers the dynamic content of the site, namely, the blog posts that we create. Each file is a separate post, and by default Jekyll supports Markdown and HTML format for these - however, this can be extended to other file formats with a little work.

The filenames of the posts are important, however. The post needs the format

YEAR-MONTH-DAY-title.extension

The date part is in the format YYYY-MM-DD. So, to use the example post name:

2016-02-14-welcome-to-jekyll.markdown

All posts begin with a 'front matter' - a section of YAML code that defines how the file should get processed by Jekyll as the site is built. The YAML block is marked out by triple dashes, and the code goes between these lines:
{% highlight yaml %}
---
layout: post
title:  "Welcome to Jekyll!"
date:   2016-02-14 20:44:43 +0800
categories: jekyll update
---
{% endhighlight %}
The above is from the default post.

*As a quick aside, posts can be created in draft format, but putting them in a `_drafts` folder created at the ame level as _posts. These are not included in the site build by default, but can be output using the flag `-D` or `--drafts` on the `jekyll serve` command.* 

When it comes to the nitty-gritty of actually writing the post, and the day-to-day of managing the blog, you rather inevitably start to have to learn specific syntaxes and rules for how to work. For example, Jekyll can automatically generate an excerpt for a post that you can output elsewhere on the site. By default, the excerpt picks up the first paragraph element, and you can drop that onto a page using
{% highlight liquid %}{% raw %}
{{ page.excerpt }}
{% endraw %}{% endhighlight %}
the excerpt output onto the page will be wrapped in a <p> element. Which can be removed with an extra bit of Liquid
{% highlight liquid %}{% raw %}
{{ page.excerpt | remove: '<p> | remove : '</p>' }}
{% endraw %}{% endhighlight %}
And if you don't like the default paragraph selection, then you can define a part of the document - add a 'excerpt_separator' in the YAML, and use this in the post
{% highlight yaml %}
---
excerpt_separator: <!--more-->
---
{% endhighlight %}

and in the actual post  
```
    In the excerpt      
    <!-- more -->  
    Not in the excerpt
```  
So... it's possible, Jekyll is fairly flexible in what you can do with it, but there's a little overhead in learning the specific syntax. There will of course be specific stuff to learn with any new tool, and I suppose the ideal is to keep that stuff minimal and rational - you should be able to appreciate why a particular feature works a particular way, and avoid too many 'just because' non-explanations. And for the most part, so far, Jekyll seems to do this.
