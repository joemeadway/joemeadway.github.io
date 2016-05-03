---
layout: post
title:  "Languages supported by Rouge syntax highlighter"
date:   2016-05-02 20:35:00 +0800
categories: jekyll rouge
---

Rouge is used by Jekyll to provide syntax highlighting in code blocks, demarcated with curly braces, and the keyword `highlight` followed by the name of the syntax to highlight. 

For example, to highlight C# code, one would use `{% raw %}{% highlight csharp %}{% endraw %}`, and close the block with `{% raw %}{% endhighlight %}{% endraw %}`, which outputs something like:

{% highlight csharp %}

public void MethodName(string parameterName)
{
    //something or other

}

{% endhighlight %}

It's worth noting that to output highlighted Liquid code, you need to use the `raw` tag, in effect to escape the code - otherwise Liquid will try and process the nested code. For example, to output

{% highlight liquid %}{% raw %}

{% highlight liquid %}
{% endhighlight %}

{% endraw %}{% endhighlight %}

one needs an opening `{% raw %}{% highlight liquid %}{% endraw %}` tag, followed by `{% raw %}{% raw %}{% endraw %}`, and closed with `endhighight` and `endraw`. (And that sentence in turn needed them, and presumably it's `raw` tags all the way down).

A full list of supported syntaxes is available [here][rouge-supported-syntaxes].

[rouge-supported-syntaxes]: https://github.com/jneen/rouge/wiki/list-of-supported-languages-and-lexers
