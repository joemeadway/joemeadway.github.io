---
layout: post
title:  "What does Jekyll use the date in the filename for?"
date:   2016-03-12 20:00:28 +0800
categories: jekyll
---

The [Jekyll documentation][jekyll-docs-filename] states that you need to name posts in the format

> YYYY-MM-DD-title.extension

and it's not initially explained why. Looking into the default sample project, the obvious answer would be that the date here builds the folder structure - in the sample project the post file is name

> '2016-02-12-welcome-to-jekyll.markdown'

(taking the date it was created), and this builds into the site structure

> /jekyll/update/2016/2/12/welcome-to-jekyll.html

so it's obviously defining the folder structure of the site. Except when it's not. Because if you change the date in that default filename, the folder structure won't change - 

> 2016-02-14-welcome-to-jekyll.markdown 

will still build to 

> /jekyll/update/2016/2/12/welcome-to-jekyll.html

How so? In that default post, there's also a 'date' parameter in the Front Matter, set to the timestamp of when the site/post was generated - in my case '2016-02-12 20:44:43 +0800'. And if you change *this* date to 2016-02-14 20:44:43 +0800, *then* the folder structure will output /jekyll/update/2016/2/14/welcome-to-jekyll.html. 

But the file name date doesn't quite do nothing. If you remove it, and just have 'welcome-to-jekyll.markdown', then Jekyll won't generate the post at all. And if you comment out the 'date' variable, then the file name date *does* define the post's date.

A brief aside: the post date itself affects a few things. For example:
- the `post.date` of the post, which Liquid can output
- whether the post is ready to be generated - if post date > today, then it won't generate
- the site structure

It's all a bit clumsy - rather like one convention has replaced another, but without removing all the dependencies on the old convention in the Jekyll engine. And it seems from this [Github issue closed back in 2012][github-issue-120] that there's no real desire to change it. The advice seems to be that if you don't like the date being set in the filename, then you should use '0000-00-00-title.extension' - which rather seems to miss the point. However, the problem is an aesthetic one, and I can understand why it may not be a priority to fix. Instead, it seems like a decent starting point for digging into the codebase a little and trying to change it, as one of the comment on that Github issue mentions.

Until then will have to remember the following:

- Date the filename - even if you don't use it to structure your site, it will make sorting through a folder full of posts easier
- When generating the post, Jekyll will
     - look for the number pattern 'dddd-dd-dd-' in the filename, and generate any posts that match
     - set the `post.date` using the date variable in the Front Matter, if present
     - if not, set the `post.date` using the file name date
     - if there is no date variable, and the filename is an invalid date (such as '0000-00-00'), then throw an error on compilation

[jekyll-docs-filename]: https://jekyllrb.com/docs/posts/#creating-post-files
[github-issue-120]: https://github.com/jekyll/jekyll/issues/120