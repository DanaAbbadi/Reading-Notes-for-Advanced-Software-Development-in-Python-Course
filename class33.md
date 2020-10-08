# React Router

React Router keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling built right in. Make the URL your first thought, not an after-thought.

**Installation**

You can install React Router from the public npm registry with either npm or yarn. 

```
npm install react-router-dom
```

## React - Styling FAQ

CSS-in-JS refers to a pattern where CSS is composed using JavaScript instead of defined in external files.

Note that this functionality is not a part of React, but provided by third-party libraries. React does not have an opinion about how styles are defined; if in doubt, a good starting point is to define your styles in a separate *.css file as usual and refer to them using className.

## NextJs 

#### Create a Next.js App

To build a complete web application with React from scratch, there are many important details you need to consider:

Code has to be bundled using a bundler like webpack and transformed using a compiler like Babel.
You need to do production optimizations such as code splitting.
You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering.
You might have to write some server-side code to connect your React app to your data store.
A framework can solve these problems. But such a framework must have the right level of abstraction — otherwise it won’t be very useful. It also needs to have great “Developer Experience”.

#### Next.js: The React Framework

Next.js has the best-in-class “Developer Experience” and many built-in features; a sample of them are:

* An intuitive page-based routing system (with support for dynamic routes)
* Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis
* Automatic code splitting for faster page loads
* Client-side routing with optimized prefetching
* Built-in CSS and Sass support, and support for any CSS-in-JS library
* Development environment with Fast Refresh support
* API routes to build API endpoints with Serverless Functions
* Fully extendable

Next.js is used in tens of thousands of production-facing websites and web applications, including many of the world’s largest brands.