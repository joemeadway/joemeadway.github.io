---
layout: post
title:  "Installing npm on Windows"
date:   2016-03-20 13:24:28 +0800
categories: NodeJS npm winodws
---

npm is included with Node, but out of curiosity I ran

```
clist npm
```

with Chocolatey, which returns npm as an available option... But! the package at <https://chocolatey.org/packages/npm> has a deprecation notice. (As an aside, would it be possible to mark packages as deprecated on the returned list?) Anyway, to install Node

```
cinst nodejs.install
```

But! It looks like there's an improved way of keeping npm up-to-date, by using a neat package called 'npm-windows-upgrade': <https://github.com/felixrieseberg/npm-windows-upgrade>. According to the GitHub page, it was developed by folks at Microsoft to fix a problem where Powershell & CMD failed to find the new version of npm after an upgrade.

Install with

```
npm install -g npm-windows-upgrade
```

And run the update with

```
npm-windows-upgrade
```

There are also command options - so for example you can specify a specific version of npm to upgrade or downgrade to.
