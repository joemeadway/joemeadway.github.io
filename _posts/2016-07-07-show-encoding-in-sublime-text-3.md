---
layout: post
title:  "How to show encoding in Sublime Text 3"
date:   2016-07-07 11:16:00 +0800
categories: sublime-text encoding tips
---

Found that Sublime Text doesn't show the file encoding by default, which can sometimes be awkward. Can be [fixed](http://stackoverflow.com/questions/21289157/set-encoding-of-file-to-utf8-with-bom-in-sublime-text-3) to do so as follows:

In Sublime Text, navigate to `Preferences > Settings - Users`. This corresponds to the `Preferences.sublime-settings` file in the relevant app data folder that ST uses. This is a JSON object, into which add `"show_encoding":true`. The current file encoding will show in the bottom right corner of the ST window.  