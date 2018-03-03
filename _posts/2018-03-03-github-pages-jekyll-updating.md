---
layout: post
title:  "Updating Github Pages Jekyll configuration"
date:   2018-03-03 13:25:00 +0800
categories: jekyll github-pages
---

Hadn't updated for a while, and prompted to doso by the Github vulnerable dependency alert. So, how to?

```
bundle update
```

I then also had to add an explicit line in the gemfile for timezone info

```
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
```

and run 

```
bundle install
```

Presumably there's some dependency that's slightly awry between the last time updated and now, since the tzinfo version included in github-pages (or a subdependency somewhere along the line) default bundle was `1.2.5`, vs. the `1.2018.3` current version that came down after.