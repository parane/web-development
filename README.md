# Javascript Eco system #

![Alt Text](asset/javascript.png)


## Nodejs ##

- JavaScript runtime environment
- runs on the V8 JavaScript engine
- executes JavaScript code outside a web browser.

![Alt Text](asset/node.jpg)

## Frontend Tools ##

![Alt Text](asset/eco.jpg)

In modern web development, Node is increasingly used to run tools and services
depended on by front-end engineers. As a Node programmer, you may be responsible
for setting up and maintaining these tools. As a full-stack developer, you’ll want to use
these tools to create faster and more reliable web applications

https://www.linux.com/training-tutorials/modern-day-front-end-development-stack/

The benefits of using front-end build systems can be huge. They can help you to write
more readable and future-proof code. There’s no need to worry about ES2015 browser
support when you can transpile it with Babel. Also, because you can generate source
maps, browser-based debugging is still possible.


Recently, front-end and server-side developers have converged on using npm for
distributing JavaScript. That means npm is used for frontend modules, such as React,
and serverside code, such as next js.

### Babel ###
Babel is transpilar which are used to convert modern ecmascript  into more widely supported ES5 code.

https://babeljs.io/

### Npm ###
#### Package manager ###
npm (Node Package Manager) is the default package manager for Node.js. It is used to manage and share JavaScript code by providing a repository for Node.js packages/modules. npm allows developers to install, share, and manage dependencies for their projects.

<pre>npm install express </pre>
<pre>npm uninstall express </pre>
<pre>npm publish </pre>

#### Script Running: ####
npm has built-in features for running scripts. Therefore, you can rely on your collaborators or users being able to invoke commands such as npm
start and npm test. To add your own command for npm start, you add it to the scripts property of your project’s package.json file

<pre>npm run build </pre>

### Front end build tool  ###

#### Old Players Gulp & Webpack #### 
Gulp - A toolkit for automating time-consuming tasks in your development workflow.
Webpack is a module bundler. Its main purpose is to bundle JavaScript files for usage in a browser, yet it is also capable of transforming, bundling, or packaging just about any resource or asset.


#### Vite ####
Vite is the new player in the town, but the interesting fact is that it outperforms Webpack in terms of speed. It was developed by Evan You, creator of Vue.js.

A build tool that aims to provide a faster and leaner development experience for modern web projects.

https://dev.to/debajit13/vite-vs-webpack-a-comparative-analysis-851
https://ritza.co/articles/gen-articles/webpack-vs-babel-vs-rollup-vs-gulp-vs-parcel-vs-vite/