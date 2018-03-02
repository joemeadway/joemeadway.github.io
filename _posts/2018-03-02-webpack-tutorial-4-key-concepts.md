---
layout: post
title:  "Webpack Official Tutorial Notes - 4 Key Concepts"
date:   2017-03-02
 14:31:00 +0800
categories: webpack
---

Webpack is a tool to compile javascript modules. When setup on a project, it will look through the files of that project, and piece together all the dependencies that each needs. It will then output all of those dependencies into a bundle.

4 Key Concepts
---

- **Entry**  
An entry point sets where webpack should begin its dependency graph. 

- **Output**  
The ouput defines where the bundles webpack creates should be emitted.

- **Loaders**  
Loaders are used by webpack to handle different types of input files - they generally convert input files into formats that webpack can process. For example, css, sass, images, fonts, etc. Loaders generally use `test` to indicate which files should be transformed; and `use` to indicate which loader should handle these files.

- **Plugins**  
Plugins are used to extend the default functionality of webpack. For example, they may minify content, or optimise images - things that webpack will not do on its own.

All of these get setup in the `webpack.config.js` file.
