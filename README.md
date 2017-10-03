# React Sandbox

Anirudh learns react....

## Setup

To get the basic implementation of our application to work we need to load some dependancies. One popular packager manager for JavaScript is NPM. We will be using NPM to load what outside libraries we need for our application to work. We do this by creating a package.json that lists what packages the project depends on.  

To install those packages, run at root of project:

```
$ npm install
```

At present the following are the packages we are relying on:

### Babel

[Babel](https://babeljs.io) is a javascript compiler used to compile
'next' generation JavaScript (es6), and a few other JS language extension to
JavaScript that browsers support. For us we will be converting our
`src/app.js`, which is written in
[JSX](https://reactjs.org/docs/jsx-in-depth.html) and ES6. React code
does not need to be written with either of these, but is much easier
with them. Right now our Babel is used by [webpack](https://webpack.js.org/) so the browser
compliant js is hidden from us, but if you want to see what that
conversion looks like then you can use the Babel [CLI](https://babeljs.io/docs/usage/cli/):

```
$ node_modules/babel-cli/bin/babel.js src/app.js
``` 

This will print the converted JS to the console. You'll notice the
JS it spits out is *almost* browser compliant. Everything, but the
require lines:

```
var _react = require('react');
...
```

That's because Babel (or at least the presets we are using) don't know
how to convert require, which is a way that the new JS has utilized to
manage dependancies outside of using `<script src="./node_modules/react/"...` in the html. To handle that and open us up to using a lot of other cool js building things we are using Webpack. 

*Note we don't need Webpack to use require. We could load a package like
[requirejs] to handle managing our js files. We could also use other
build tools.*

### Webpack

We are using Webpack as our js build tool. It will: 
1. convert our JSX/ES6 to ES5 (using Babel) 
2. bundle our code (basically sorting out those `import...from..)`
3. and spit it out all the js we need into one big file `dist/bundle.js`

## Run

```
$ npm start
```
