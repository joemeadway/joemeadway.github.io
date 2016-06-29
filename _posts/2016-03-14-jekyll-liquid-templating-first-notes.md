---
layout: post
title:  "Jekyll using Liquid templating - first notes"
date:   2016-03-14 18:00:28 +0800
categories: jekyll liquid
---
Jekyll uses the Liquid templating engine to generate pages. Useful things that templating enables include the reduction of repeated code through use of snippets; the insertion of dynamic variables when the site is generated; and conditional layouts dependent on arbitrary logical tests. We've seen these used elsewhere, with examples from the default example site.

Liquid was developed by Shopify as a means of dynamically rendering content with data from a database. There's quite a neat contrast is uses here - in Shopify to render content dynamically, and Jekyll to render static content, but both using the same engine to actually render the content. In Jekyll, instead of dynamically loading variables from an external source, we set them in the `_config.yaml`, in the Front Matter. 

On top of these Liquid uses tags, objects and filters to build up pages. Not going to go into the detail of everything available (documentation for Liquid here: <https://docs.shopify.com/themes/liquid> and for Jekyll-using-Liquid here: <http://jekyllrb.com/docs/templates/>), but rather run through a very brief overview such that these things can actually be recognised for what they are when seen in the wild. 

Tags mark out the logic that tells the engine what to do; tags are found within the `{% raw %}{% %}{% endraw %}` marks, and offer function such as logical control, iteration over variables, and theming. 'include', which we've seen previously, is a theme tag.
 
Objects contain the content variables;  there are many default objects defined. Global objects are accessible from any file, and include things like 'template'. There are a lot specific to developing shopify websites (such as 'cart'). There are also non-global default objects, such as 'page' and 'handle'.

Filters modify the output of strings, etc. that are being output onto the page. They're placed in `{{ }}` marks, and there are various types for strings, HTML, Maths, inter alia. Of particular use are probably the Array filters, allowing us to join, index, map, sort, etc. arrays of data; HTML filters that can be used to shorthand generate tags, such as `<img>` and `<script>`;  JSON, for outputting a property in JSON format...

Jekyll implements all the standard tags and filters, and adds a few extras on top - `{% raw %}{{ site.time | date_to_xmlschema }}{% endraw %}` outputs the given date in the ISO 8601 XML Schema format; `{% raw %}{{ "string of something" | slugify }}{% endraw %}` outputs a slug of the input, "string-of-something". There are quite a few custom bits added by Jekyll, and advanced use of the tool will use plenty of these in quite complicated configurations.  

