---
layout: post
title:  "Transpiling JS"
date:   2017-09-26 12:05:28 +0800
categories: dev-environment-setup configuration node-js babel pluralsight
---

Transpiling is necessary for 
- using the newer features of ES6+ during development, while outputting the older, widely supported, ES5 JavaScript in the browser
- using languages that offer supersets/alternatives to JavaScript, such as CoffeeScript of Typescript

Lots of options, e.g.
- Babel
- Typescript
- Elm

**Babel** allows use of modern, experimental JS features not yet implemented in most/all browsers; it transpiles written code into ES5-compliant output

**Typescript** is a superset of JS, predominantly aimed at introducing type saftey to JS development

**Elm** is also a superset of JS, with the aim of providing a functional language that compiles to JS

The appeal of Elm and Typescript is probably clear - both type safety and a functional approach can remove a lot of the runtime errors that plain js can produce - objects missing methods or properties, removing null references, etc. etc. But, focus on Babel here.
- allows wrting of satandard JS, and leverage full JS ecosystem without plugins
- can get experimental features sooner
- no need for type definitions - less overhead
- ES6 is statically analysable, which will allow for type safety checks 

Babel configuration
---

Configuring Babel can be done in the `package.json` file, but typically add a `.babelrc` file in the project root folder.

Babel then included by adding the relevant packages into `package.json`, e.g.
```
"babel-cli": "6.16.0",
"babel-core": "6.17.0",
"babel-loader": "6.2.5",
"babel-preset-latest": "6.16.0",
"babel-register": "6.16.3",
```
and call babel in the npm scripts calling `babel-node` vs. the original `node`.


*Write up of notes from Pluralsight: Building a JavaScript Development Environment*