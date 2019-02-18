<div  align="center">
<img  width="150"  height="150"  src="http://funkyimg.com/i/2RrmN.png">
<h1>Webpack Starter Kit</h1>
<p>
:fire: A simple <strong>webpack 4 starter project</strong> for your basic web development needs.
</p>
</div>

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [FAQ](#faq)

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

## Prerequisites

* [Node.js](https://nodejs.org) > 7.6

## Getting Started

The easiest way to get started is to clone the repository:

```bash
# Get the latest stable release
git clone https://github.com/Jandyk/webpack-starter-kit.git PROJECT-NAME

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

### Where's the common webpack config?

**There is none and that is good thing.**

The pattern creates unnecessary confusion over the setup, at the end the config will always be different across environments.
People just put booleans everywhere on the common config to switch between these differing configuration options which is just awful to see and confusing for someone who's just starting on webpack.

The only truly shared config between these files are the entry js point and the main html template.

### How to load images

#### In JavaScript

You can require an image from JavaScript like
```js
const myImage = require('./assets/img/icon.png');
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
const myImage = require('!!url!/assets/img/icon.png');
```

#### In `index.html`

If you would like to include an image on your `index.html` file, place the path of the image in a webpack require statement`<%= require(imagePath) %>`.

```html
  <img class="webpack-logo"
       src="<%= require('./src/assets/img/webpack.png') %>"
       alt="webpack logo"></a>
```

## License

The code is available under the [MIT License](LICENSE).

---
Thanks for reading! 🙏
