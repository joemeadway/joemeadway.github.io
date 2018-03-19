---
layout: post
title:  "Webpack Official Tutorial Notes - Development"
date:   2018-03-19 14:30:00 +0800
categories: webpack
---

Tools to make the development environment better. Not to be used in production.

Source Maps
---

Source maps make it easier to track down errors and warnings.

When multiple files are bundled into one `bundle.js` file, when something goes wrong the stack trace will just point to this bundled file - it won't actually be clear which file included in the bundle is the source of the error.

A source map maps the code in the bundled file back to the original input files.

There are lots of [different options](https://webpack.js.org/configuration/devtool/), with varying trade offs between output and speed of compilation. As a rule of thumb, look for speed of compilation over bundle size for development, and favour plugins that produce separate source maps and support minimisation for production.

