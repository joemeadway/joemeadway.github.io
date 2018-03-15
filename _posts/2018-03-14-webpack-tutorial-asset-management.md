---
layout: post
title:  "Webpack Official Tutorial Notes - Asset Management"
date:   2018-03-14 14:15:00 +0800
categories: webpack
---

Webpack can dynamically bundle dependencies into Javascript modules, but it can also bundle up almost any other type of file and include it in the *dependency graph*. The result of this is that we can have a sophisticated picture of all the interlinked dependencies of any particular aspect of a website, be it js, CSS, external data, images, fonts, etc.

Each different file type that is bundled up needs a `loader` that knows how to handle that type.

Loading CSS
---

For CSS, you need to add the `style-loader` and `css-loader` into the configuration.

Loaders can be added in the same way as any npm module

```
npm install --save-dev style-loader css-loader
```

and gets added into the config using something like:

```
module: {
    rules: [
        {
            test: /\.css$/,
            use: [
                'style-loader',
                'css-loader'
            ]
        }
    ]
}
```

Files are picked up using the regular expression in the `test` property. When this is in place, we can use `import` a css file just like we did the js file, and the stringified css is added into the output file.

e.g.
This (in style.css)

```
.hello {
    color: red;
  }
```

Referenced in index.js

```
import './style.css';

...

element.classList.add('hello');
```

means that webpack outputs the following into bundle.js

```
exports.push([module.i, ".hello {\r\n    color: red;\r\n  }\r\n  ", ""]);
```

CSS can be fairly easily split into smaller constituent parts, and only the relevant bit loaded for each page; loaders are also available for sass, less, postcss, etc.

At this point, the nature of webpack is becoming apparent - it really is a tool for *modular* front end development. Because that output of css-into-a-javascript-file is really quite peculiar, and really only makes sense if you see the whole project in terms of the conistituent parts. There's a good Stack Overflow answer making this point here: [https://stackoverflow.com/a/35347634](https://stackoverflow.com/a/35347634).

Loading Images
---

We can load images using `file-loader`.

```
{
    test: /\.(png|svg|jpg|gif)$/,
    use: [
        'file-loader'
    ]
}
```

And then we can import an image into a module

```
import MyImage from './my-image.png'
```

As part of the bundling, webpack copies the image into the output directory, and also sets MyImage to reference the URL of the image. By default the image is also renamed to something guid-ish.

Loading Fonts
---

For fonts, we use the `file-loader` loader again, but targeting different file extensions - e.g.

{% highlight javascript %}

{
    test: /\.(woff|woff2|eot|ttf|otf)$/,
    use: [
        'file-loader'
    ]
}

{% endhighlight %}

and reference in the css

{% highlight css %}

@font-face {
    font-family: 'MyFont';
    src:  url('./my-font.woff2') format('woff2'),
    url('./my-font.woff') format('woff');
    font-weight: 600;
    font-style: normal;
}

.hello {
    color: red;
    -family: 'MyFont';
    background: url('./icon.png');
}

{% endhighlight %}

Loading Data
---
We can also load data files in variety of formats - JSON, XML, CSV, etc. There are usually different loaders for the data type being loaded - `csv-loader`, `xml-loader`...

{% highlight javascript %}

{
    test: /\.(csv|tsv)$/,
    use: [
        'csv-loader'
    ]
},
{
    test: /\.xml$/,
    use: [
        'xml-loader'
    ]
}

{% endhighlight %}

Component file structure
---

Using all these imports mean it can be very straighforward to apply the comonent structure right through a project - we simply rely on relative references to import the necessary parts into the relevant .js files. e.g.

```
|– /components
|  |– /my-component
|  |  |– index.jsx
|  |  |– index.css
|  |  |– icon.svg
|  |  |– img.png
```

Here, `index.jsx` would simply reference the icon.svg, img.png etc., and is easily transferrable to different projects, as long as that project has the releavant loaders defined in the project configuration.

We can also maintain a more traditional project structure, for exmaple

```
|– /src
|  |– /js
|  |  |– index.js
|  |– /img
|  |  |– icon.png
|  |– /css
|  |  |– style.css
```

Here, `index.js` simply references the relevant files; however this structure is less easily transferred.