# [React Components](https://www.theodinproject.com/lessons/node-path-react-new-react-components)

## Introduction

In this lesson, we'll be going over the basics of React components - what they do, and how to write them. Make sure to use the project you set up in the previous lesson, but try not to copy and paste any code while you're coding along.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Learn about React components.

- Understand how to create components.

- Describe where components reside in a React project.

<br>

## What are components?

The beauty of React is that it allows you to break a UI (User Interface) down into independent reusable chunks, which we will refer to as components. The following picture should give you an idea of how to do that when building a very basic app.

![](images/1.png)

For example, this website could be broken into the following components:

- `App`, which represents your main application and will be the parent of all other components.

- `Navbar`, which will be the navigation bar.

- `MainArticle`, which will be the component that renders your main content.

- `NewsletterForm`, which is a form that lets a user input their email to receive the weekly newsletter.

Think of these reusable chunks as JavaScript functions which can take some kind of input and return a React element.

<br>

## How to create components

To get the feel of working with components, we're going to practice creating functional components. What are functional components? JavaScript functions! Let's have a look.

```js
function Greeting() {
	return (
		<h1>&quot;I swear by my pretty floral bonnet, I will end you.&quot;</h1>
	)
}
```

This might look mostly familiar to you - it's a JavaScript function, which returns JSX. Open up the project you were working on, create a new file named `Greeting.jsx`, and in that file write your own handmade functional component. Name it whatever you wish, and have it return whatever JSX you wish.

Are you done? Check the naming of your function! Is it capitalized? Keep this key difference in mind. **React components must be capitalized** or they will not function as expected, which is why we capitalized `Greeting()`. More about that later.

> **HTML escape code**
>
> In the above example, `&quot;` is an escape code we use to render `"`. You linter will greet you with an error if you use regular quotes. You can use this [LambdaTest tool for escaping HTML characters](https://www.lambdatest.com/free-online-tools/html-escape) if you run into such errors, or you can read more about [HTML escape codes](https://www.w3.org/wiki/Common_HTML_entities_used_for_typography).

<br>

### What is HTML doing in my JavaScript?

It's JSX. It look jarring at first, but soon we'll realize how cool it is. We'll learn all about it in the upcoming lessons!

<br>

## Where do components live

So remember how our component is just hanging out in its own dedicated file? This makes it independent from the rest of the codebase! That said, while independence is great, we do want the component to use functionality created elsewhere, and to share itself with other components. How can we do this? `import`ing and `export`ing! For a very long time in React development, it was necessary to `import` React in your JavaScript files that used React components, but since React v17.0 it is no longer required. Let's `export` our newly created component so that parent components can use it as a child throughout your project.

```js
function Greeting() {
	return (
		<h1>&quot;I swear by my pretty floral bonnet, I will end you.&quot;</h1>
	)
}

export default Greeting
```

Are we done? Well let's think about this - we've declared our component, and exported it, but does `main.jsx` know about it yet? Nope! Let's fix that. Let's look at `main.jsx`, we can see that `render()` is rendering the `App` component. Let's replace that `App` component with our newly created greeting, which we'll have to make sure is first imported properly. The end result should look something like this:

```js
import { StrictMode } from "react"
import { createRoot } from "react-dom/client"
import App from "./App.jsx"
import Greeting from "./Greeting.jsx"
import "./index.css"

createRoot(document.getElementById("root")).render(
	<StrictMode>
		<Greeting />
	</StrictMode>
)
```

Remember that `<Greeting />` should be capitalized! Try using lower case for the import, function name and component and see what happens! When the JSX is parsed, React uses the capitalization to tell the difference between an HTML tag and an instance of a React component. `<greeting />` would be interpreted as a normal HTML element with no special meaning, instead of your shiny new React component.

Otherwise, just like that, you've successfully imported and used your first custom-made component, congratulations!

<br>

## Knowledge check

- **What does a React element look like?**

It looks like a JavaScript function expression with an capitalized name.

<br>

- **How would you create a functional component?**

You create a functional component by creating its own .jsx file, declaring the component name capitalized, and exporting it. The capital letter is what indicates that it's a React component rather than a normal HTML tag.

<br>

- **How do you export and then import a component?**

`export default ComponentName` and `import ComponentName from 'ComponentName.jsx`

<hr>
<br>
<br>

# [export](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#description)

The `export` declaration is used to export values from a JavaScript module. Exported values can then be imported into other programs with the `import` declaration or dynamic import. The value of an imported binding is subject to change in the module that exports it -- when a module updates the value of a binding that it exports, the update will be visible in its imported value.

In order to use the `export` declaration in a source file, the file must be interpreted by the runtime as a module. In HTML, this is done by adding `type="module"` to the `<script>` tag, or by being imported by another module. Modules are automatically interpreted in strict mode.

<br>

## Syntax

```js
// Exporting declarations
export let name1, name2 /*, ... */; // also var
export const name1 = 1, name2 = 2 /*, ... */; // also var, lte
export function functionName() { /* ... */ }
export class ClassName { /* ... */ }
export function* generatorFunctionName() { /* ... */ }
export const { name1, name2: bar } = o;
export const [ name1, name2 ] = array;

// Export list
export { name1, /* ... */ nameN };
export { variable1 as name1, variable2 as name2, /* ... */, nameN }
export { variable1 as "string name" };
export { name1 as default /* ... */ };

// Default exports
export default expression;
export default function functionName() { /* ... */ }
export default class ClassName { /* ... */ }
export default function* generatorFunctionName() { /* ... */ }
export default function () { /* ... */ }
export default class { /* ... */ }
export default function* () { /* ... */ }

// Aggregating modules
export * from "module-name";
export * as name1 from "module-name";
export { name1, /* ... */ nameN } from "module-name";
export { import1 as name1, import2 as name2, /* ... */ nameN } from "module-name";
export { default, /* ... */ } from "module-name";
export { default as name1 } from "module-name";
```

`nameN` - Identifier to be exported (so that it can be imported via `import` in another script). If you use an alias with `as`, the actual exported name can be specified as a string literal, which may not be a valid identifier.

<br>

## Description

Every module can have to different types of export, _named export_ and _default export_. You can have multiple named exports per module but only one default export. Each type corresponds to one of the above syntax.

Named exports:

```js
// export features declared elsewhere
export { myFunction2, myVariable2 }

// export individual features (can export var, let,
// const, function, class)
export let myVariable = Math.sqrt(2)
export function myFunction() {
	// ...
}
```

After the `export` keyword, you can use `let`, `const`, and `var` declarations, as well as function or class declarations. You can also use the `export { name1, name2 }` syntax to export a list of names declared elsewhere. Note that `export {}` does not export an empty objet - it's a no-op declaration that exports nothing (an empty name list);

Export declarations are not subject to [temporal dead zone](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#temporal_dead_zone_tdz) rules. You can declare that the module exports `X` before the name `X` itself is declared.

```js
export { x }
const x = 1
// This works, because `export` in only a declaration, but doesn't
// utilize the value of `x`.
```

Default exports:

```js
// export feature declared elsewhere as default
export { myFunction as default };
// This is equivalent to:
export default myFunction;

// export individual features as default
export default function () { /* ... */}
export default class { /* ... */ }
```

> **Note:** Names for export declarations must be distinct from each other. Having exports with duplicate names or using more than one `default` export will result in a `SyntaxError` and prevent the module from being evaluated.

The `export default` syntax allows any expression.

```js
export default 1 + 1
```

As a special case, functions and classes are exported as _declarations_, not expressions, and these declarations can be anonymous. This means functions will be hoisted.

```js
// Works because `foo` is a function declaration,
// not a function expression
foo();

export default function foo() {
  console.log("Hi");
}

// It's still technically a declaration, but it's allowed
// to be anonymous
export default function () {
  console.log("Hi");
}
```

Named exports are useful when you need to export several values. When importing this module, named exports must be referred to by the exact same name (optionally renaming it with `as`), but the default export can be imported with any name. For example:

```js
// file.test.js
const k = 12
export default k
```

```js
// some other file
import m from "./test" // note that we have the freedom to use import m instead of import k, because k was default export
console.log(m) // 12
```

You can also rename named exports to avoid naming conflicts:

```js
export { myFunction as function1, myVariable as variable }
```

You can rename a name to something that's not a valid identifier by using a string-literal. For example:

```js
export { myFunction as "my-function" }
```

<br>

## Re-exporting / Aggregating

A module can also "relay" values exported from other modules without the hassle of writing two separate import/export statements. This is often useful when creating a single module concentrating various exports from various module (usually called a "barrel module").

This can be achieved with the "export from" syntax:

```js
export { default as function1, function2 } from "bar.js"
```

Which is comparable to a combination of import and export, except that `function1` and `function2` do not become available inside the current module:

```js
import { default as function1, function2 } from "bar.js"
export { function1, function2 }
```

Most of the "import from" syntaxes have "export from" counterparts.

```js
export { x } from "mod"
export { x as v } from "mod"
export * as ns from "mod"
```

There is also `export * from "mod"`, although there's no `import * from "mod"`. This re-exports all **named** exports from `mod` as the named exports of the current module, but the default export of `mod` is not re-exported. If there are two wildcard exports statements that implicitly re-export the same name, neither one is re-exported.

```js
// -- mod1.js --
export const a = 1

// -- mod2.js --
export const a = 3

// -- barrel.js --
export * from "./mod1.js"
export * from "./mod2.js"

// -- main.js --
import * as ns from "./barrel.js"
console.log(ns.a) // undefined
```

Attempting to import the duplicate name directly will throw an error.

```js
import { a } from "./barrel.js"
// SyntaxError: The requested module './barrel.js' contains conflicting star exports for name 'a'
```

The following is syntactically invalid despite its import equivalent:

```js
export DefaultExport from "bar.js" // invalid
```

The correct way of doing this is to rename the export:

```js
export { default as DefaultExport } from "bar.js"
```

The "export from" syntax allows the `as` token to be omitted, which makes the default export still re-exported as default export.

```js
export { default, function2 } from "bar.js"
```

`export from` supports all features that `import` supports - for example, import attributes:

```js
export { default } from "./data.json" with { type: "json" }
```

<br>

## Examples

### Using named exports

In a module `my-module.js`, we could include the following code:

```js
// module "my-module.js"
function cube(x) {
	return x * x * x
}

const foo = Math.PI + Math.SQRT2

const graph = {
	options: {
		color: "white",
		thickness: "2px",
	},
	draw() {
		console.log("From graph draw function")
	},
}

export { cube, foo, graph }
```

Then in the top-level module included in your HTML page, we could have:

```js
import { cube, foo, graph } from "./my-module.js"

graph.options = {
	color: "blue",
	thickness: "3px",
}

graph.draw() // Logs "From graph draw function"
console.log(cube(3)) // 27
console.log(foo) // 4.555806215962888
```

It is important to note the following:

- You need to include this script in your HTML with a `<script>` element of `type="module"`, so that it gets recognized as a module and dealt with appropriately.

- You can't run JS modules via a `file://` URL -- you'll get CORS errors. You need to run it via an HTTP server.

<br>

### Using the default export

If we want to export a single value representing an entire module, we could use a default export:

```js
// module "cube.js"

export default function cube(x) {
	return x * x * x
}
```

Then, in another script, it is straightforward to import the default export:

```js
import cube from "./cube.js"
console.log(cube(3)) // 27
```

<br>

### Using export from

Let's take an example where we have the following hierarchy:

- `childModule1.js`: exporting `myFunction` and `myVariable`

- `childModule2.js`: exporting `MyClass`

- `parentModule.js`: acting as an aggregator (and doing nothing else)

- top level module: consuming the exports of `parentModule.js`

This is what it would look like using code snippets:

```js
// In childModule1.js
function myFunction() {
	console.log("Hello!")
}
const myVariable = 1
export { myFunction, myVariable }
```

```js
// In childModule2.js
class MyClass {
	constructor(x) {
		this.x = x
	}
}

export { MyClass }
```

```js
// In parentModule.js
// Only aggregating the exports from childModule1 and childModule2
// to re-export them
export { myFunction, myVariable } from "childModule1.js"
export { MyClass } from "childModule2.js"
```

```js
// In top-level module
// We can consume the exports from a single module since parentModule
// "collected"/"bundled" them in a single source
import { myFunction, myVariable, MyClass } from "parentModule.js"
```
