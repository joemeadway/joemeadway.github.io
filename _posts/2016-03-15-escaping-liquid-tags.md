---
layout: post
title:  "Escaping Liquid tags"
date:   2016-03-15 20:44:00 +0800
categories: liquid jekyll
---

Apart from using the `raw` and `endraw` tags, liquid tags can also be escaped using quotation marks - but the syntax for doing so is cumbersome. In short, you need to wrap the thing to be escaped in double-curly-braces-space-quotation-mark:

```liquid
{% raw %} {{ " <escaped bit> " }}  {% endraw %}
```

So for example:

```liquid
{% raw %}{{ "{% this " }}%} {% endraw %}
```

Outputs {% raw %} `{% this %}` {% endraw %}. Or perhaps

```liquid
{% raw %} {{ "{{ this " }}}}  {% endraw %}
```

to output {% raw %}`{{ this }}`{% endraw %}

Source: <http://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags>
