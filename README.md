<div align="center">
  <img src="https://user-images.githubusercontent.com/46722214/52979148-00757f00-33dd-11e9-8019-96677c0dbca7.png">
  <h1>Webpack Boilerplate</h1>
  <p>
    :fire: A professional front-end template for building fast, robust, and adaptable web apps or sites with the best developer experience and a focus on performance and best practices.
  </p>
</div>

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [FAQ](#faq)
  * [When should I use this starter?](#when-should-i-use-this-starter)
  * [How to load images](#how-to-load-images)
    + [In JavaScript](#in-javascript)
    + [In HTML](#in-html)
  * [How to include Bootstrap in your project](#installing-bootstrap)
  * [How to include jQuery in your project](#installing-jquery)
- [License](#license)

## Features

* Separated development and production webpack settings you can understand
* Sass
* ES6
* Asset loading
* CSS Vendor prefixing
* Development server
* Sourcemaps
* Favicons generation
* Production optimizations
* Normalize.css and helpers
* High performance

## Prerequisites

* [Node.js](https://nodejs.org) > 7.6

## Getting Started

The easiest way to get started is to clone the repository:

```bash
# Get the latest stable release
git clone https://github.com/Jandyk/webpack-boilerplate.git PROJECT-NAME

# Change directory
cd PROJECT-NAME

# Install NPM dependencies
npm install
```

To start the development server

```bash
npm start
```

To build for production

```bash
npm run build
```

To preview the production build

```bash
npm run preview
```

## FAQ

### When should I use this starter?

You should use this starter if any of the following are true:

* You want to make a static page. e.g. splash screen, onboarding screen, phaser game, threejs visualization, countdown.
* You found no good starter kit for whatever you want to do and need a solid place to start from.

### How to load images

#### In JavaScript

You can require an image from JavaScript like
```js
const myImage = require('./assets/favicon/icon.png');
```

If the image size in bytes is smaller than `8192`you, `myImage` will be a string with the encoded image path such as 
```
data:image/svg+xml;base64,bW9kdWxlLmV4cG9ydHMgPSBfX3dlYnBhY2tfcHVibGljX3BhdGhfXyArICJhc3NldHMvaW1hZ2VzL3RpY2stQ3lydkhSdi5zdmciOw==
```
If the image size is larger than `8192` it will be a string with the url to the image such as 
```
src/assets/icon.png?hash=5b1f36bc41ab31f5b801
```

This limit is set so images like icons are not loaded through a request but you can force the loader to give you image urls always by doing the following but should not be necessary. The limit works 90% of the time.
```js
const myImage = require('!!url!/assets/favicon/icon.png');
```

#### In HTML

If you would like to include an image on your `index.html` file, place the path of the image in a webpack require statement`<%= require(imagePath) %>`.

```html
<img src="<%= require('./src/assets/img/rocket.png') %>" alt="rocket">
```

### Installing Bootstrap

Bootstrap is dependent on [jQuery](https://jquery.com/) and [Popper](https://popper.js.org/), these are defined as `peerDependencies`, this means that you will have to make sure to add both of them to your `package.json` using `npm install --save jquery popper.js`.

Then install bootstrap as a Node.js module using npm.

```bash
npm install --save bootstrap
```

**Importing JavaScript**

Import Bootstrap’s JavaScript by adding this line to your app’s entry point `index.js`:

```js
import 'bootstrap';
```

Alternatively, you may **import plugins individually** as needed:

```js
import 'bootstrap/js/dist/util';
import 'bootstrap/js/dist/alert';
...
```

**Importing Styles**

Importing Precompiled Sass in the `style.scss`:

```scss
@import "~bootstrap/scss/bootstrap";
```

### Installing jQuery

Install jQuery as a Node.js module using npm.

```bash
npm install --save jquery
```

In `webpack.dev.js` and `webpack.prod.js`, add the following to require the webpack at the very top before any other code:

```js
const webpack = require('webpack');
```

To automatically load jquery we can simply point both variables it exposes to the corresponding node module, in `webpack.dev.js` and `webpack.prod.js` add the following code:

```js
plugins: [
  new webpack.ProvidePlugin({
    $: 'jquery',
    jQuery: 'jquery'
  });
  ...
]
```

Then in `index.js` or any of our source code add the following code:

```js
// in a module
$('#item'); // <= just works
jQuery('#item'); // <= just works
// $ is automatically set to the exports of module "jquery"
```

## License

The code is available under the [MIT License](LICENSE).

---
Thanks for reading! :pray:
<div>Made with :heart:</div>
