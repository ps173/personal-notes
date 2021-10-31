# Guide to express middlewares

## A basic definition

Express middlewares are the functions that have access to the `request`, `response`
and `next` function in applications request response cycle. The `next` function calls
the next middleware that is succeding the current middleware.

Let's simplify the above statement a bit. So a express middleware is basically a function
that has req,res and next as a parameters. For example,

```js
const express = require("express");
const app = express();

function logger(req, res, next) {
  console.log("I am a middleware and I log the text");
  next();
}
app.use(logger);
app.get("/", (req, res) => {
  res.send("Hellow World!!");
});
app.listen(3000);
```

Now here I have a `logger` function which is a middleware. Yup that's how simple a middleware
can be. Here the `logger` function has one thing which other functions don't have.
You **always** have to call `next` at the end of the middleware. This basically invokes the next or succeding middleware.
For example

```js
function logger1(req, res, next) {
  console.log("I am first");
  next();
}

function logger2(req, res, next) {
  console.log("I am second");
  next();
}

app.use(logger1);
app.use(logger2);
```

here logger1 is the first middleware and the logger2 is next or succeding middleware.
This of course depends on the which function is loaded first in `app.use()`.So now whenever
express calls a callback then these 2 middlewares will do a `console.log()` before
running that callback. If I was to load the logger2 before logger1 then logger2 will `console log` before logger1.

for example if I add this to last line of previous code then.

```js
app.get("/", (req, res) => {
  res.send("Hellow World!!");
  console.log("I am a callback");
});
// output in the console will be
// I am first
// I am second
// I am a callback
```

The `next` function could be named anything else either but by convention it is always named `next`. So to provide
any confusion we continue calling it next. **Also remeber if you don't call `next()` at the end of the middleware then the middleware will never
go to the next or succeding middleware. This means the request will left hanging and will never proceed**

## Example : Using a middleware to get a object from database

In my app I use following middleware to get a snippet by a certain id provided in a request.
This can give you a gist of where to use a middleware.

```js
function getSnippetById(req, res, next) {
  let snippet;
  try {
    // here Snippets is mongoose schema.
    snippet = await Snippets.findById(req.params.id);
    if (snippet == null) {
      return res.status(404).json({
        message: "question does not exist",
      });
    }
  } catch (err) {
    res.status(401).json({ message: err.message });
  }

  res.snippet = snippet;
  next();
}
```

In this middleware I simply check for the snippet in database if it does not exists
we return a error other wise I attach the snippet with give header. Now here snippet
keyword is a custom header that I provide which I can access in the callback further.
for example if I do

```js
app.get("/:id", getSnippetById, (req, res) => {
  res.status(200).json(res.snippet);
});
```

now here I didn't use app.use instead I called the middleware directly inside the
get request. This is useful because app.use will call the function `getSnippetById` before
every request which is not what we want. So instead we call it only for some function
such as when we want to delete, update or get a object(in this case snippet) by a certain id.

I should also mention something called as a **error-handling middleware** which depends on same concept.
You can see more about error handling middleware [here](https://expressjs.com/en/guide/error-handling.html).

# Conclusion

So we went over how the middlewares are called, what is next function and what happens when we
don't call it and also we went over a real world example of a middleware too. To read a better
and a detailed explanation [checkout the express docs on writing a middleware](https://expressjs.com/en/guide/writing-middleware.html)
and also on [using a middleware](https://expressjs.com/en/guide/using-middleware.html)
