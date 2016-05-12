---
layout: post
title:  "Setting up Jekyll with Gituhub Pages on Windows"
date:   2016-04-23 22:24:28 +0800
categories: jekyll github-pages windows
---

There was a similar error on Windows, where multiple ruby gems couldn't be built. The actual error message was 
{% highlight shell %}
Gem::InstallError: The 'json' native gem requires installed build tools.
{% endhighlight %}
And again, a very useful error message was given:
{% highlight shell %}
Please update your PATH to include build tools or download the DevKit
from 'http://rubyinstaller.org/downloads' and follow the instructions
at 'http://github.com/oneclick/rubyinstaller/wiki/Development-Kit'
{% endhighlight %}
According to that Github page, the Ruby Development Kit was developed in order to make Ruby development on Windows easier. [https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#devkit-background](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit#devkit-background) - it aims to provide a consistent starting point for Ruby developers working on Windows. This will likely be superseded once bash-on-windows is widely available, and Windows developers will be able to compile using the Ruby compiler sitting in a linux environment, but until then...

But following the instructions at the Github link worked neatly - the only awkward bit was working out where the relevant Ruby installation was - having downloaded a few different versions over time, and farily lost track of them. However, running
{% highlight shell %}
gem env
{% endhighlight %}
lists out a whole host of details about the environment that the active Ruby installation is running, including the `INSTALLATION DIRECTORY`, which was the folder location that needed to be listed in the dev kit config file.
