---
layout: post
title:  "The default Jekyll site structure"
date:   2016-02-16 20:15:28 +0800
categories: jekyll
---

The default output from
{% highlight bash %}
jekyl new
{% endhighlight %}
outputs everything - the 'generating' templating files and the 'generated' output into one folder. In this, the actual site content is generated in the folder `_site`

One can give a specific destination folder for these output files using the `--destination` flag. This will just output the site files to that folder, where it is perhaps easier to see the structure of generation back end stuff vs. generated front end stuff.

Default site includes:

```
About
     -index.html
css
     -main.css
jekyll
     -update
          -<year>
               -<month>
                    -<day>
                         -welcome-to-jekyll.html
feed.xml
index.html
```

Should all be fairly obvious what each part is doing - welcome-to-jekyll.html is the actual posted content of the site, and this is automatically rolled up into the RSS-compatible feed.xml

Key of course is how this corresponds to the templating files that generate this output:

```
.sass-cache
_includes
     -footer.html
     -head.html
     -header.html
     -icon-github.html
_posts
     -yyyy-mm-dd-welcome-to-jekyll.markdown
_sass
     -_sass-partial-files.scss
_site
css
     -main.scss
.gitignore
_config.yml
about.md
feed.xml
index.html
```
