# Exploring Web Components And How can you get started using them in your website

# Wild Intro AKA State of web

Well I have been hearing a lot of "web has been exploited by the bloat of
javascript frameworks", or that web is not easy to work with any more and we
need to change the way build websites and go back to plain and traditional html
and css. In a recent [video by Rich Harris](https://youtu.be/860d8usGC0o) ( a great talk by the way please check it out)
he mentions a new way to build the web apps which he quotes "transitional webapps" which he believes will become a new
approach to web development in possible future. Also many people say that web technologies are fine and the state
[package management is a hot mess](https://nadh.in/blog/javascript-ecosystem-software-development-are-a-hot-mess/) which certainly is correct.

All of this aside we still need to create and serve user experience (UX)
without making our html hard to understand and read and also keeping the
components interactive. Cool. That's the reason we have javascript. Is it right
to keep html in javascript or is it right to have a template that we can use to
generate html? IDK. I will leave that on the other [elders](https://www.urbandictionary.com/define.php?term=Technological%20Boomer) to decide.
I will continue exploring until I have seen enough and I am one of those elders.

Nonetheless the weird and wild intro aside, everything above was just to get you
engaged and now since you all are engaged, So I am gonna chatter about web components.

# The Real Web Components

Firstly I may define which web components are we talking about. I am not talking
about the components that we use in react or angular or svelte. I am talking about the
REAL Web Components.

So in [some blog](https://viljamis.com/2019/why-we-use-web-components/) I read a definition which I think defines these web components in most poetic way.

> We had the urge to create a tech-agnostic instead of tech-specific system. A system that is based on web standards and would survive the births and deaths of JavaScript frameworks.

So these web components are a set of web platform apis that allow you to create custom and reusable
html tags to use in your webpages and webapps. To understand them better one needs to know these terms

- [**Shadow DOM**](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM) : Shadow DOM is a set of javascript apis that can be used to attach a encapuslated "shadow"
  DOM tree to an element. This provides a way to keep the styles and scripts of a element private.

- [**Custom ELement**](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements) : Custom elements are again set of javascript apis used to define custom elements and
  their behaviour. So suppose you want a text area component in your app. Your requirement is that your text area should
  have line numbers. So you can create a custom element to extend it with your provided styles. (we will take a look
  at this example further in the article.)

- [**HTML templates**](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_templates_and_slots) : The `<template>` and `<slot>` elements allow you to write markup that can be reapeated easily.

With these terms out now we can get into how to make web components.

So do you remember we talked about making a web component that is a text area and has a line height well let's make that. So I will start by making a html file.
let's call this `index.html` and the contents of file will be these

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Custom Text Area</title>
  </head>
  <body>
    <custom-textarea></custom-textarea>
    <script src="./CustomTextarea.js"></script>
  </body>
</html>
```

```js
// js code here
```

There are advantages of webcomponents over other frameworks. Specifically these advantages being :

1. Web components make it easier to reduce the complexity of our design system.

2. Web components can be embeded with either any frameworks or they can be used alone without any frameworks.
   This gives web components a huge advantage as they don't require you to bend your preferences.

3. Shadow dom allows the components to have their own DOM Tree which is not accessed by main document.
   This leads to better encapsulation

# WIP (More Soon)

# side note / personal experience

I made my personal website in webcomponents and It does not uses any external
libraries and relies solely on the browser supported stuff. Obviously it is not
minified and I can go a step further and minify my code using webpack and then
make a new branch on gh-pages and then render that minified thing out for
better performance but that would not effect the site loading by larger margins
the personal website is as snappy as ever. Also I did use google lighthouse and
the site performance was 74. which can be improved further by minifying
javascript

---

Links for further reading :

1. https://duetds.github.io/date-picker/
2. https://www.webcomponents.org/introduction#what-are-web-components-
3. https://changelog.com/jsparty/6
4. https://viljamis.com/2019/why-we-use-web-components/
5. https://stenciljs.com/
6. https://lit.dev/
7. https://blog.logrocket.com/what-happened-to-web-components/