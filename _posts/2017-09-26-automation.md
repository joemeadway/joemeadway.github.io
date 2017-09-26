---
layout: post
title:  "Automating build steps with npm scripts"
date:   2017-09-26 14:05:28 +0800
categories: dev-environment-setup configuration node-js npm
---

Numerous options for automating build steps
- grunt
- gulp
- npm scripts

**Grunt** 
- the original
- aim is for configuration over code
- plenty of plugins
- writes output to a file as it goes along

**Gulp**
- uses pipes - in-memory streams - instead of writing to files
- faster
- goes for code over configuration - javascript methods
- even more plugins

**npm scripts**
- declare in 'scripts' section of `package.json`
- leverage OS command line
- use npm package directly - all of npm is available
- can call out to separate node scripts
- simpler debugging?
- de facto standard?

Scripts take npm commands, such as `start` and `test`, and points them to node scripts, e.g. a line in `package.json` could look like

`"start": "npm run app.js"`

Also has built-in pre- and post-tasks - the prefixes pre-/post- will always run before/after the script of the same name.

Npm scripts don't require global modules.

Concurrent tasks can be run with `npm-run-all`, e.g.

`npm-run-all --parallel security-check open:src` 

What's happening here? 

`npm-run-all`: this runs multiple tasks  
`--parallel`: flag to run them in parallel  
`security-check` and `open:src`: the tasks to run, also defined in `package.json`  
`security-check` is a task that calls to `nsp`, a package that scans node code for common security issues  
`open:src` is a task that starts the express server for local running  

*Write up of notes from Pluralsight: Building a JavaScript Development Environment*