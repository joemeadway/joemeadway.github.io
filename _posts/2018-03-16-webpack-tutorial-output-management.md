---
layout: post
title:  "Webpack Official Tutorial Notes - Output Management"
date:   2018-03-16 09:50:00 +0800
categories: webpack
---

As projects grow, it can get difficult to keep track of multiple bundles, especially if they have hashes in the filenames. There are plugins to make managing this easier.

We can define multiple entry points in the config

```
entry: {
    app: './src/index.js',
    print: './src/print.js'
},
```

and then have these output to separate files:

```
output: {
    filename: '[name].bundle.js',
    path: path.resolve(__dirname, 'dist')
}
```

this outputs the name of the entry point as the filename - e.g. `app.bundle.js`.

It then can become difficult to import the correctly named files. To fix this we can use HtmlWebpackPlugin.

```
npm install --save-dev html-webpack-plugin
```

and in the config
```
const HtmlWebpackPlugin = require('html-webpack-plugin');

...

plugins: [
    new HtmlWebpackPlugin({
        title: 'Output Management'
    })
],
```
This plugin generates its own index.html, and will overwrite any that we already have. It will have all the bundles automatically added.

Clean up the dist folder with `clean-webpack-plugin` - this will clear out the dist folder before each build.