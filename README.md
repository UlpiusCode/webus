<div align="center">
  <img src="https://user-images.githubusercontent.com/46722214/52979148-00757f00-33dd-11e9-8019-96677c0dbca7.png">
  <h1>Webpack Boilerplate</h1>
  <p>
    :fire: A professional front-end template for building fast, robust, and adaptable web apps or sites with the best developer experience and a focus on performance and best practices.
  </p>
</div>

## :bookmark_tabs: Table of Contents

- [Introduction](#wave-introduction)
- [Features](#bulb-features)
- [Prerequisites](#wrench-prerequisites)
- [Getting Started](#rocket-getting-started)
- [Documentation](#book-documentation)
  * [How to load images](#how-to-load-images)
    + [In JavaScript](#in-javascript)
    + [In HTML](#in-html)
  * [How to include Bootstrap in your project](#installing-bootstrap)
  * [How to include jQuery in your project](#installing-jquery)
- [License](#key-license)

## :wave: Introduction

**Webpack Boilerplate** is a Starter Kit for building user interfaces.

## :bulb: Features

* Separated development and production webpack settings you can understand
* ES6
* Sass
* Asset loading
* CSS Vendor prefixing
* Development server
* Sourcemaps
* Normalize.css and helpers
* Favicons generation
* Production optimizations
* High performance

## :wrench: Prerequisites

* [Node.js](https://nodejs.org) > 7.6

## :rocket: Getting Started

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

## :book: Documentation

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

## :key: License

The code is available under the [MIT License](LICENSE).

---
Thanks for reading! :pray:
<div>Made with :heart:</div>
