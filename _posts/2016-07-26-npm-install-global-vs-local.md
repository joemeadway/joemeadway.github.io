---
layout: post
title:  "npm install - global or local"
date:   2016-07-26 15:17:00 +0800
categories: node-js npm snippets
---

A quick note so I don't forget/can find it later - a rule of thumb for whether an npm package installs globally or locally:

> If you want to use it as a command line tool, something like the grunt CLI, then you want to install it globally. On the other hand, if you want to depend on the package from your own module using something like Node's `require`, then you want to install locally.
>
> -- <https://docs.npmjs.com/getting-started/installing-npm-packages-globally>
