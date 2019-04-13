# visjs-network

A dynamic, browser-based network visualization library. A network-visualization focused fork of the visualization library [vis.js](https://github.com/visjs-community/vis)

visjs-network is designed to be easy to use, handle dynamic data, and enable data manipulation.
The library consists of the following components:

- Network. Display a network (force directed graph) with nodes and edges.
- DataSet and DataView. A flexible key/value based data set. Add, update, and
  remove items. Subscribe on changes in the data set. A DataSet can filter and
  order items, and convert fields of items.
- DataView. A filtered and/or formatted view on a DataSet.

## Install

Install via yarn:

    yarn add visjs-network

Install via npm:

    npm install visjs-network

Install via bower:

    bower install visjs-network

Or download the library from the github project:
[https://github.com/visjs-community/visjs-network.git](https://github.com/visjs-community/visjs-network.git).

## Load

To use a component, include the javascript and css files of vis in your web page:

```html
<!DOCTYPE HTML>
<html>
<head>
  <script src="webroot/vis/dist/vis.js"></script>
  <link href="webroot/vis/dist/vis.css" rel="stylesheet" type="text/css" />
</head>
<body>
  <script type="text/javascript">
    // ... load a visualization
  </script>
</body>
</html>
```

or load vis.js using require.js. Note that vis.css must be loaded too.

```js
require.config({
  paths: {
    vis: 'path/to/vis/dist'
  }
})
require(['vis'], function(math) {
  // ... load a visualization
})
```

## Examples

```bash
yarn examples
```

Run the `yarn examples` command to explore the examples locally.  This command launches a local server, opens a browser window, and navigates that browser window to the index page for the top-level examples directory.

Examples can be
found in the [examples/](https://github.com/visjs-community/visjs-network/tree/master/examples) directory
of the project.

## Build

To build the library from source, clone the project from github

    git clone git://github.com/visjs-community/visjs-network.git

The source code uses the module style of node (require and module.exports) to
organize dependencies. To install all dependencies and build the library,
run `yarn` or `npm install` in the root of the project.

    cd vis
    yarn

Then, the project can be built by running:

    yarn build

To automatically rebuild on changes in the source files, once can use

    yarn watch

This will both build and minify the library on changes. Minifying is relatively
slow, so when only the non-minified library is needed, one can use the
`watch-dev` script instead:

    yarn watch-dev

## Custom builds

The folder `dist` contains bundled versions of vis.js for direct use in the browser. These bundles contain all the visualizations and include external dependencies such as _hammer.js_ and _moment.js_.

The source code of vis.js consists of commonjs modules, which makes it possible to create custom bundles using tools like [Browserify](http://browserify.org/) or [Webpack](http://webpack.github.io/). This can be useful when bundling vis.js as part of your own browserified web application.

_Note that hammer.js version 2 is required as of v4._

### Prerequisites

Before you can do a custom build:

- Install _node.js_ and _npm_ on your system: https://nodejs.org/
- Install _yarn_ on your system: https://yarnpkg.com/en/
- Install the following modules globally using yarn: `browserify`, `babelify`, and `uglify-js`:

  ```
  yarn global add browserify babelify uglify-js
  ```

- Download or clone the vis.js project:

  ```
  git clone https://github.com/visjs-community/visjs-network.git
  ```

- Install the dependencies of vis.js by running `yarn` or `npm install` in the root of the project:

  ```
  cd vis
  npm install
  ```

### Examples of custom builds

#### Example 1: Exclude external libraries

The default bundle `vis.js` is standalone and includes external dependencies such as _hammer.js_ and _moment.js_. When these libraries are already loaded by the application, vis.js does not need to include these dependencies itself too. To build a custom bundle of vis.js excluding _moment.js_ and _hammer.js_, run browserify in the root of the project:

    browserify index.js -t [ babelify --presets [env] ] -o dist/vis-custom.js -s vis -x moment -x hammerjs

This will generate a custom bundle _vis-custom.js_, which exposes the namespace `vis`, and has _moment.js_ and _hammer.js_ excluded. The generated bundle can be minified with uglifyjs:

    uglifyjs dist/vis-custom.js -o dist/vis-custom.min.js

The custom bundle can now be loaded as:

```html
<!DOCTYPE HTML>
<html>
<head>
  <!-- load external dependencies -->
  <script src="http://cdnjs.cloudflare.com/ajax/libs/moment.js/2.17.1/moment.min.js"></script>
  <script src="http://cdnjs.cloudflare.com/ajax/libs/hammer.js/2.0.8/hammer.min.js"></script>

  <!-- load vis.js -->
  <script src="dist/vis-custom.min.js"></script>
  <link href="dist/vis.min.css" rel="stylesheet" type="text/css" />
</head>
<body>
  ...
</body>
</html>
```

## Test

To test the library, install the project dependencies once:

    yarn

Then run the tests:

    yarn test

## Contribute

[Contributions](https://github.com/visjs-community/visjs-network/blob/master/misc/how_to_help.md) to the vis.js library are very welcome!

### Contributors

This project exists thanks to all the people who already contributed.
<a href="graphs/contributors"><img src="https://opencollective.com/vis/contributors.svg?width=890" /></a>

## History

See this [github issue comment](https://github.com/visjs-community/visjs-network/issues/4015#issuecomment-410556365) for some project history.

The vis.js library was originally developed by Dutch R&D Company [Almende B.V](http://almende.com).

## License

Copyright (C) 2010-2018 Contributors

Vis.js is dual licensed under both

- The Apache 2.0 License
  http://www.apache.org/licenses/LICENSE-2.0

and

- The MIT License
  http://opensource.org/licenses/MIT

Vis.js may be distributed under either license.
