# Understanding about webpack

Webpack is a module bundler similar to [rollup.js](rollupjs.org/guide/en) , [snowpack](https://www.snowpack.dev/) or [parcel](https://parceljs.org/).
According to webpack site :

> At its core, webpack is a static module bundler for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph from one or more entry points and then combines every module your project needs into one or more bundles, which are static assets to serve your content from.

### What does a module bundler does btw and Why do we need it ?

At it's core it minifies your code to run faster and better in browser. It
generates a big chunk of minified code which includes all the imported
functions you have in a one file(not really I have seen more than one file
sometimes).

Also module bundler is required because:

-   Browser do not support module system, although this is not entirely true.

-   It helps you manage dependencies effectively and keeping the app fast

-   It helps you to load your assets in dependency order, image asset, css asset, etc.

Some resources :.

1. [this great blog](https://dev.to/alexeagleson/understanding-the-modern-web-stack-webpack-part-1-2mn1)
2. [Webpack Documentation](https://webpack.js.org/concepts/)
3. [what is a module bundler and how does it work](https://lihautan.com/what-is-module-bundler-and-how-does-it-work/)
