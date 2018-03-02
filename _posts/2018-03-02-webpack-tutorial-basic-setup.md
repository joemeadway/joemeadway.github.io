---
layout: post
title:  "Webpack Official Tutorial Notes - Basic Setup"
date:   2018-03-02 09:05:00 +0800
categories: webpack
---

Basic Setup
---

Requires the `webpack` npm package

```
npm install --save-dev webpack
```

Once installed, we can begin to create bundles. Generally, we would separate a project into two, the `src` and the `dist`. `src` is the collection of files input into webpack; `dist` is the destination for the bundles output by webpack.

External dependencies would be imported into our js files using the `import` statement, e.g.

```
import _ from 'lodash';
```

`import` is in ES2015, but not yet standard in most browsers. Webpack transpiles it to make it usable across different browsers. N.B. webpack doesn't by default transpile any other code, so a transpiler such as Babel would be required.

And, our homegrown .js files would be bundled up, so we would also update our references to these, e.g.

```
<script src="bundle.js"></script>
```

or whatever the bundle is called...

Then, at it's most basic, we run the `npx webpack` command to kick the process off

```
npx webpack [entry point] --output [output location], e.g.
npx webpack src/index.js --output dist/bundle.js
```


A Configuration
---

We can add a configuration file to specify behaviour in a more complex setup. It not only removes the need for inputting a lot of commands into the CLI, but also make the webpack process consistent across each time it's run across different environments.

So, for our entry point/output location CLI parameters, we can use:

```
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  }
};
```

NPM Scripts
---

We can add a script into the `package.json` file to run an npm script to do our webpack build.

```
{
  ...
  "scripts": {
    "build": "webpack"
  },
  ...
}
```

this will be called with `npm run build`, and trigger the webpack bundling as we did previously using `npx`. This allows (as with including the configuration) more consistency across different build environments.
