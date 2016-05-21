---
layout: post
title:  "An assortment of errors found setting up Jekyll with Github pages on Ubuntu"
date:   2016-04-22 20:00:00 +0800
categories: jekyll github-pages
---

Setting up Jekyll to use with Github pages, following the guide here:

[https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)

All fairly straightforward until the `bundle install` step, at which point a couple of packages failed to install - the first was showing an error installing RedCloth, and is the same as here:

[https://github.com/jekyll/jekyll/issues/3737](https://github.com/jekyll/jekyll/issues/3737)

And the fix - to install the `ruby-dev` package - worked too.

The second was a little more fiddly, but mostly because I misread the error message (or more accurately, skimmed it and latched onto what looked like the most pertinent information...)

The error showed the package `nokogiri` was failing to build, and searching on this took me round a few different fix suggestions, such as this:

[https://github.com/sparklemotion/nokogiri/issues/1166](https://github.com/sparklemotion/nokogiri/issues/1166)

which has you install using specified system libraries for the zip part of the build. This didn't fix it, so after time spent installing various versions of libxml2 to no avail, it was back to the error message...

Which rather helpfully described the problem was that `zlib` was missing. And lo and behold, searching on this error turned up

[https://github.com/flapjack/omnibus-flapjack/issues/72](https://github.com/flapjack/omnibus-flapjack/issues/72)

which advised

```
sudo apt-get install zlib1g-dev
```

which allowed `bundle install` to run as advertised.

Finally, the last command

```
bundle exec jekyll serve
```

failed, with the error

```
ERROR: YOUR SITE COULD NOT BE BUILT:
------------------------------------
No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository.
```

To fix, needed to add the repository name to a 'repository' variable in `_config.yml` - I put the url of the github repository in here, but given this didn't exist yet it possibly doesn't matter what the value here is? Irregardless, the build succeeded, hurrah and hurray.
 
(Although I should be honest and point out that immediately after upgrading my Ubuntu to 16.04, the bundle fails to run entirely - an environment error saying that the Ruby2.1 path can't be found. I've always been using Ruby2.3 on the Ubuntu VM I have running, so... well, I'm back to building on Windows for the time being.)
