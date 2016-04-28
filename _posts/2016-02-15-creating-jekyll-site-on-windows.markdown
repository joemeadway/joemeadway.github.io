---
layout: post
title:  "Why Jekyll? And quick setup on Windows"
date:   2016-02-15 21:24:28 +0800
categories: jekyll
---


There were a few technical reasons for choing to use Jekyll for this blog:

- Github integration seems allows neat 'merge and push a new post' updating
- Want to see more Ruby in action, and want to get hands properly dirty with Markdown
- Intrigued by static website generators, want to dig in to how they work a bit more

And a non-technical reason

- Having the blog post commits highlighted in green on my github profile... More posts, more green - struck me as a good motivator, rather like Jerry Seinfeld's crossing-days-off-a-calendar technique for getting something done

(though this does illustrate an inherent problem with the that display - there's a certain vanity and peacocking to having a nice green commit history, but quantity isn't quality)

Seems easiest to start with Chocolatey...
{% highlight shell %}
cinst ruby -y
{% endhighlight %}
then
{% highlight shell %}
gem install jekyll
{% endhighlight %}
And then after opening a new console window

{% highlight shell %}
jekyll new .
{% endhighlight %}
creates the new site
{% highlight shell %}
jekyll serve
{% endhighlight %}
starts running a localhost server on port 4000 by default. 

A lot of older posts about setting up Jekyll suggest there will be problems with the encoding of the files - that Ruby or Jekyll will not use UTF-8 by default on Windows. On Jekyll version > 1.3 you can set the encoding as a parameter in the _config.yaml file... alternatively, setting the console encoding every time it runs... However, running Jekyll 3.1.1 on Ruby 2.2.3, I haven't found any problems with this as yet, so assume this is something that doesn't affect later versions of Ruby or Jekyll (whichever was causing the problem in the first place). Indeed, generated files appear to be UTF-8 encoded without BOM.
