# Trying Out Svelte For First Time

So I have been wanting to re-create my personal [website](ps173.github.io) (another blog on this soon).
I really like development with next-js. But there's a lot of lot of dependencies 
which makes it quite a huge app. And I think that a personal website 
should be as fast as possible. So why not choose something like vanilla html.
Well Yea html will work totally fine. But I wanted to try something new.
I choose svelte as a the other framework. I wanted to try it for the longest
time. And thus I choose svelte.

I like lot of stuff about svelte. The idea of keeping things less complex and fast to code is
very likeable. If I would have tried using svelte right after learning js,
I think it would be easier than getting used to react. Here's my opinion or more
of a description of svelte. I might be wrong about something so pardon me there as
I have spent less than a week with svelte.

Also Since I have made the intro this long. I might just say that I don't really want to hate on other
framework. I think this [opinionism](https://www.urbandictionary.com/define.php?term=opinionism) is bad 
I just want to keep this a healthy overview of svelte.

# About Svelte ✌️

Svelte is a UI framework. Unlike react and friends (or should I say enemies), 
svelte does not use any virtual DOM. Rather it compiles your code to tiny framework less vanilla js.
This makes the app really fast. 

Also not to mentiont the incredible guide the [svelte-tutorial](https://svelte.dev/tutorial/basics)

# Components in Svelte 🐻‍❄️ 

So let's start with what I think the makes all the frameworks worth using,
Components. I think making your UI into little components makes UI really easy
to manage and program. I am not a frontend guy honestly but I like the fact that 
I can have multiple elements divided in my UI. Again this post is not on why 
frontend frameworks are good. 

In svelte the components are files with .svelte extension. Not a great change
that's just another syntax ( also btw why do all these frameworks create their
own custom syntax).  But wait you don't have to export the components here. 
Suppose you have this parent called `App.svelte`.

```svelte
<!--Lets' call this component App.svelte and yes this is a html comment-->
<script>
// here is js comment :)
 import MyComponent from "path-to-component/MyComponent.svelte"
</script>

<MyComponent />
```

and here's `MyComponent.svelte`: 

```svelte
<!--- MyComponent.svelte --->
<p>
This is my component
</p>
```

# Props in Svelte 🐻 

You thought that svelte does not have props.  Svelte has export statements to 
export props or as I like to say 'recognize props' (Not a proper term don't use it).

This is a child component let's call it `Weatherdetails.svelte`

```svelte 
<!--- Weatherdetails.svelte --->
<script>
	export let answer;
</script>

<p>The weather is {answer}</p>
```

Let's call the parent component `App.svelte`.

```svelte
<script>
	import Weatherdetails from './Weatherdetails.svelte';
</script>

<Weatherdetails answer="humid :\"/>
```

I like how svelte devs explain how this in not javascript-ish.

> this may feel a little weird at first. That's not how export
> normally works in JavaScript modules! Just roll with it for now — it'll soon
> become second nature.

I am hoping to see it become second nature :)

# Reactivity in Svelte 🐨

Again as svelte describes it does not uses any complex state management.
According to the svelte website "At heart of svelte is a powerful system of
reactivity". This means that you can call javascript inside your html (not
literally I just like to think of it this way). Here's the reactivity explained
in the good ol' counter app.

```svelte
<script>
let counter = 0
function increaseCount(){
  count += 1
}
</script>

<h1> Current Count : {count} </h1>
<button on:click={increaseCount}> 
    click to increase count ! 
</button>
```
Wow that was quick.

Here you can see it's like react state just has a lot less boiler-plate.
Also svelte introduces a special thing which is somewhat similar to `useEffect` 
hook in react.

```svelte
<script>
let counter = 0
function increaseCount(){
  count += 1
}
$: square = count * count
</script>

<h1> Current Count : {count} </h1>
<button on:click={increaseCount}> 
    click to increase count ! 
</button>
<p>The square of {count} is {square} </p>
```
**Here the `$` looks a little weird. But this basically tells svelte compiler
that whenever any of referenced value statement changes do this thing.** 

# Conditional rendering and Await in markup 🐑

To render text conditionally svelte applies a little bit custom markup syntax. 

```svelte
<script>
	let user = { loggedIn: false };

	function toggle() {
		user.loggedIn = !user.loggedIn;
	}
</script>

{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{:else}
	<button on:click={toggle}>
		Log in
	</button>
{/if}
```

So here according to svelte website again 
>A # character always indicates a block opening tag. 
>A / character always indicates a block closing tag. 
>A : character, as in {:else}, indicates a block continuation tag. 
>Don't worry — you've already learned almost all the syntax Svelte adds to HTML.

Now this the normal part. Jinja follows same pattern. But wait we have more.
Introducing the asynchronous await in markup. Wanna see how this looks. Here

```svelte
<script>
	async function getCatImage() {
		const res = await fetch("https://api.thecatapi.com/v1/images/search");
		const jsonres = await res.json();
		const imageUrl = await jsonres[0].url

		if (res.ok) {
			return imageUrl;
		} else {
			throw new Error("No image found or something went wrong");
		}
	}

	let promise = getCatImage();

	function handleClick() {
		promise = getCatImage();
	}
</script>

<button on:click={handleClick}>
A random cat 🐈
</button>

<!-- Awaitting the response -->
{#await promise}
	<p>...waiting</p>
{:then src}
	<img {src} alt="a cat"/>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
```
Honestly I was really impressed when I first saw this. This is was so cool see.

Here's the working demo 🐈✨
<iframe src="https://codesandbox.io/embed/wandering-sunset-ejwo3?fontsize=14&hidenavigation=1&theme=dark&view=preview"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="await-svelte"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

# Lifecycle ♻️
Yay! Lifecycle methods. Lifecycle in svelte is quite similar to react. 

- The most common lifecycle method is `onMount`. This is basically a function
that is executed when component is rendered. 
- `onDestroy` is function that runs when a component is destroyed. 
- `beforeUpdate` and `afterUpdate` do what there names suggest run a function before or after the component is rendered.

These were quite similar to the lifecycle methods in react. 

The last lifecycle method is `tick`. The `tick` function is unlike other
lifecycle methods it can be called anytime. It returns a promise that resloves as soon as any pending state changes have been applied to DOM. 
**In simpler words you can say that when you want to ensure that
state immediately updates you can run `tick` function.**

# Binding the state 🐲

Do you guys remember the old class based components in react where you had to bind the 
function to specific component. Svelte does something similar but more simpler looking.

```svelte
<script>
	let name = 'world';
</script>
<input bind:value={name}>
```

this will change the value of name with input provided. The bind-action (in this case value) 
may change from element to element. 

### This Binding

One binding that applies to all is `this`. You can compare it to something like `useRef` hook from react. 
It provides you a reference to a rendered element.

For example you can do something like this ✨:
<iframe src="https://codesandbox.io/embed/intelligent-roman-7mh87?autoresize=1&fontsize=14&hidenavigation=1&theme=dark&view=preview"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="svelte-magic-drawboard"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

And now I can use canvas api just like native javascript. I really like the canvas api
and wanted to use react but I was not able to get that level of simplicity as in native js.
Svelte makes it almost similar to native js

# Store 🦄
Store is a way to manage state across the whole app. You may pass down state to children
using props but the when you have to share state across various parent components you can use 
store. A breif overview of stores can be given this way
```js
<!-- Store.js : Here we can initialize store -->
import { writable } from 'svelte/store';

export const count = writable(0);
```
```svelte
<!-- And let's subscribe this store to App.svelte -->
<!-- so I can just do --> 
<script>
import { count } from './stores.js';

let count_value;

count.subscribe(value => {
		count_value = value;
});
</script>

<h1>The count is {count_value}</h1>
```

Stores are a bit complex topic ( not really quite simple once you go through the tutorial )
And I am not gonna cover everything about them in this post. So that may be a different blog 
for different time. Meanwhile if you really wanna know just go on to the [tutorial](https://svelte.dev/tutorial/writable-stores)

# Inbuilt Transitions and animations 🐳
This one surprised me. Svelte has inbuild transitions , animation and motions. 

```svelte
<script>
	import { blur } from 'svelte/transition'
	let visible = true;
</script>

<label>
	<input type="checkbox" bind:checked={visible}>
	visible
</label>

{#if visible}
	<p transition:blur>
		Fades in and out
	</p>
{/if}
```
This piece of code shows how simple it is to implement the fade transition.  This is all I wanted from frontend frameworks. 
Isn't this amazing. I just love svelte now. There are more animation related stuff which you can
again see in the [svelte-tutorial](https://svelte.dev/tutorial/transition-events)

Here's a little navbar that I made using svelte builtin transitions :

<iframe src="https://codesandbox.io/embed/ecstatic-violet-t4rp3?autoresize=1&fontsize=14&hidenavigation=1&theme=dark&view=preview"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="simple-navbar-with-svelte"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

# Conclusion 💫

This was just a breifing of svelte. There is so much more that I didn't cover. I have already link svelte tutorial like 10 times in this blog 
so not gonna do It again. This post really helped me understand lot of stuff about svelte and also react.

What I think of svelte ? Well I think svelte is amazing. I like it and most of the developers out there like it.
It makes lot of things simpler. Obviously it does not kill all the other frameworks and Neither I will start making
making all my apps in svelte. Though this aside. I will svelte for lot of apps that I want to quickly setup. 
This is one thing that I again loved about svelte. The amount of boiler plate that goes in svelte is really low.
And not mention the app speed. The above 3 example are really fast in comparisont to those written in react or any other 
framework out there. Also I recently saw [svelte-native](https://svelte-native.technology/) which now makes me want to try it.

Overall Svelte is a amazing and lovely piece of technology. God bless the creators of svelte for making it.

Thanks for reading. Please consider following this took a huge amount of time to write. And if this helps you well don't thank me just 
follow. I post stuff like this or sometime vim related workflow.
