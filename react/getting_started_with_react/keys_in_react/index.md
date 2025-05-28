# [Keys in React](https://www.theodinproject.com/lessons/node-path-react-new-keys-in-react)

## Introduction

In this lesson, we will cover keys in React. Keys are special props for our components and we'll learn why they are used.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Learn what keys are in React and why it needs them.

- Identify examples of good and bad key usage in React applications.

<br>

## Why does React need keys?

In the upcoming lessons as you learn more about the internal workings of React, more specifically the re-rendering process, you will understand the importance of keys. For now, we will keep it short.

In the previous lesson on rendering lists, we used the `.map()` method to iterate over an array of data and return a list of elements. Now imagine, if any of the items in the list were to change, how would React know which item to update?

If the list were to change, one of two things _should_ happen:

1. we completely re-render the entire list, or:

2. we hunt down the specific items that were changed and only re-render those.

Assuming we want to hunt down that one specific item that was changed and NOT re-render the entire list, we need something to track that specific item. We can track down a specific item by using a `key`.

When the list is updated for whatever reason (either from a server or a user interaction), React matches the `keys` of each of the previous list items to the updated list. If there were any changes, React will only update the items that have changed.

As long as `keys` remain consistent and unique, React can handle the DOM effectively and efficiently.

<br>

## Using keys

> We will be using `props` here, and you will learn more about them in the next lesson. For now, you just need to know that `props` are arguments that are passed into components.

Keys are passed into the component or a DOM element as a prop. You should already be familiar with the syntax.

```js
<Component key={keyValue} />
// or
<div key={keyValue} />
```

Now that we know the syntax, the next question is: what should be used as a key? Ideally, there should be some identifier that is unique to each item in the list. Most databases assign a unique id to each entry, so you shouldn't have to worry about assigning an id yourself. If you are defining data yourself, it is good practice to assign a unique `id` to each item. You can use the [crypto.randomUUID() function](https://developer.mozilla.org/en-US/docs/Web/API/Crypto/randomUUID) to generate a unique id. Let's look at an example:

```js
// a list of todos, each todo object has a task and an id
const todos = [
	{ task: 'mow the yard', id: crypto.randomUUID() },
	{ task: 'Work on Odin projects', id: crypto.randomUUID() },
	{ task: 'feed the cat', id: crypto.randomUUID() },
]

function TodoList() {
	return (
		<ul>
			{todos.map((todo) => (
				// here we are using already generated id as the key.
				<li key={todo.id}>{todo.task}</li>
			))}
		</ul>
	)
}
```

Additionally, if you're sure the list will remain unchanged throughout the application's life, you can use the array index as a key. However, this is not recommended since it can lead to confusing bugs if the list changes when items are deleted, inserted, or rearranged. You will learn more about this in the assignment section's linked article.

```js
const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']

function MonthList() {
  return (
    <ul>
      {/* here we are using the index as key */}
      {months.map((month, index) -> (<li key={index}>{month}</li>))}
    </ul>
  )
}
```

Keys are straightforward to use, though there is an anti-pattern you should be aware of. Keys should never be generated on the fly. Using `key={Math.random()}` or `key={crypto.randomUUID()}` _while_ rendering the list defeats the purpose of the key, as now a new `key` will get created for every render of the list. As shown in the above example, `key` should be inferred from the data itself.

```js
// a list of todos, each todo object has a task and an id
const todos = [
	{ task: 'mow the yard', id: crypto.randomUUID() },
	{ task: 'Work on Odin projects', id: crypto.randomUUID() },
	{ task: 'feed the cat', id: crypto.randomUUID() },
]

function TodoList() {
	return (
		<ul>
			{todos.map((todo) => (
				// DON'T do the following i.e. generating keys during render
				<li key={crypto.randomUUID()}>{todo.task}</li>
			))}
		</ul>
	)
}
```

<br>

## Conclusion

Don't fret if some of the terms covered in the lesson don't make sense yet. What's crucial right now is knowing how to use keys effectively in React. As mentioned earlier, the more you learn about React, the more you will understand the importance of keys. Furthermore, using keys is not limited to rendering lists. You might encounter use cases where keys are needed, we'll leave that for you to discover.

<br>

## Knowledge check

- **Why does React need keys?**

React need keys so it will be easier for it to recall a specific component without having to re-render the whole list of components. Keys let React uniquely identify an item between its siblings.

<br>

- **How do you use keys?**

Keys are passed to components similar to a `props` argument.

<br>

- **Where should the key value ideally come from?**

Ideally it should come from the data itself and should not be generated during the render of components.

<br>

- **When can we use an array index as the key value?**

We can use an array index as the key value if the list will not be changed or rearranged. Although this is not recommended as if it changes in the future, then it will introduce bugs.

<br>

- **What is an anti-pattern when using keys?**

An anti-pattern when using keys is generating them on the fly. It will defeat the purpose of having a key because a new key will be created for every time the list is rendered.

<hr>
<br>
<br>

# [Keeping list items in order with `key`](https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key)

> **Console**
>
> Warning: Each child in a list should have a unique "key" prop.

You need to give each array item a `key` -- a sting or a number that uniquely identifies it among other items in that array:

```js
<li key={person.id}>...</li>
```

> **Note**
>
> JSX elements directly inside a `map()` call always needs keys!

Keys tell React which array item each component corresponds to, so that it can match them up later. This becomes important if your array items can move (e.g. due to sorting), get inserted, or get deleted. A well-chosen `key` helps React infer what exactly has happened, and make the correct updates to the DOM tree.

Rather than generating keys on the fly, you should include them in your data:

```js
export const people = [
	{
		id: 0, // Used in JSX as a key
		name: 'Creola Katherine Johnson',
		profession: 'mathematician',
		accomplishment: 'spaceflight calculations',
		imageId: 'MK3eW3A',
	},
	{
		id: 1, // Used in JSX as a key
		name: 'Mario José Molina-Pasquel Henríquez',
		profession: 'chemist',
		accomplishment: 'discovery of Arctic ozone hole',
		imageId: 'mynHUSa',
	},
	{
		id: 2, // Used in JSX as a key
		name: 'Mohammad Abdus Salam',
		profession: 'physicist',
		accomplishment: 'electromagnetism theory',
		imageId: 'bE7W1ji',
	},
	{
		id: 3, // Used in JSX as a key
		name: 'Percy Lavon Julian',
		profession: 'chemist',
		accomplishment:
			'pioneering cortisone drugs, steroids and birth control pills',
		imageId: 'IOjWm71',
	},
	{
		id: 4, // Used in JSX as a key
		name: 'Subrahmanyan Chandrasekhar',
		profession: 'astrophysicist',
		accomplishment: 'white dwarf star mass calculations',
		imageId: 'lrWQx8l',
	},
]
```

<br>

## Where to get your `key`

Different sources of data provide different sources of keys:

- **Data from a database:** If your data is coming from a database, you can use the database keys/IDs, which are unique by nature.

- **Locally generated data:** If your data is generated and persisted locally (e.g. notes in a note-taking app), use an incrementing counter, `crypto.randomUUID()` or a package like `uuid` when creating items.

<br>

## Rules of keys

- **Keys must be unique among siblings.** However, it's okay to use the same keys for JSX nodes in _different_ arrays.

- **Keys must not change** or that defeats their purpose! Don't generate them while rendering.

<br>

## Why does React need keys?

Imagine that files on your desktop didn't have names. Instead, you'd refer to them by their order -- the first file, the second file, and so on. You could get used to it, but once you delete a file, it would get confusing. The second file would become the first file, the third file would become the second file, and so on.

File names in a folder and JSX keys in an array serve a similar purpose. They let us uniquely identify an item between its siblings. A well-chosen key provides more information than the position within the array. Even if the _position_ changes due to reordering, the `key` lets React identify the item throughout its lifetime.

> **Pitfall**
>
> You might be tempted to use an item's index in the array as its key. In fact, that's what React wil use if you don't specify a `key` at all. But the order in which you render items will change over time if an item is inserted, deleted, or if the array gets reordered. Index as a key often leads to subtle and confusing bugs.
>
> Similarly, do not generate keys on the fly, e.g. with `key={Math.random()}`. This will cause keys to never match up between renders, leading to all your components and DOM being recreated every time. Not only is this slow, but it will also lose any user input inside the list items. Instead, use a stable ID based on the data.
>
> Note that your components won't receive `key` as a prop. It's only used as a hint by React itself. If your component needs an ID, you have to pass it as a separate prop: `<Profile key={id} userId={id} />`.

<hr>
<br>
<br>

# Video Links

- [YouTube: Index as Key Anti-pattern](https://www.youtube.com/watch?v=xlPxnc5uUPQ)
