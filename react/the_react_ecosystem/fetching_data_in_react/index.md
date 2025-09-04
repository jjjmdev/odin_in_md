# [Fetching Data in React](https://www.theodinproject.com/lessons/node-path-react-new-fetching-data-in-react)

## Introduction

Up to this point, we have been using React to build client-side applications with interactive user interfaces, but what if we want to fetch data from the internet? In order to create full-fledged web applications, we need some way to get data from external sources and dynamically display it.

In this lesson, we'll explore the ins and outs of fetching data in React, starting with the basics of making API calls, managing component state, and handling asynchronous operations using JavaScript's `fetch` function. You've already performed data fetching in earlier projects, so some material covered in the lesson will be familiar to you. Revision doesn't hurt!

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Understand how to make fetch requests in React components.

- Catching and handling errors

- Lifting requests up the component hierarchy

<br>

## A basic fetch request

Before we dive into the specifics of fetching data in React, let's briefly revisit how we can use the fetch API to get data from a server.

```js
const image = document.querySelector('img')
fetch('https://jsonplaceholder.typicode.com/photos', {
	mode: 'cors',
})
	.then((response) => response.json())
	.then((response) => {
		image.src = response[0].url
	})
	.catch((error) => console.error(error))
```

We're making a request to the JSONPlaceholder API to retrieve an image, and then setting that URL to the src of an `<img>` element.

<br>

## Using fetch in React components

Now, let's take a look at how we can incorporate `fetch` into a React component, similar to our previous example. One common use case is to fetch data from an API when a component mounts, so that the data can be displayed on screen.

Whenever a component needs to make a request as it renders, it's often best to wrap that `fetch` inside of an effect.

```js
import { useEffect, useState } from 'react'

const Image = () => {
	const [imageURL, setImageURL] = useState(null)

	useEffect(() => {
		fetch('https://jsonplaceholder.typicode.com/photos', {
			mode: 'cors',
		})
			.then((response) => response.json())
			.then((response) => setImageUrl(response[0].url))
			.catch((error) => console.error(error))
	}, [])
}

export default Image
```

`useState` lets us add the `imageURL` state, whereas `useEffect` allows us to perform side effects. In this case, the side effect is fetching data from an external API. Since we need to fetch the data only once when the component mounts, we pass an empty dependency array.

<br>

## Handling errors

Working over the network is inherently unreliable. The API you're making a request to might be down, there could be a network connectivity issues, or the response you receive could contain errors. A multitude of things can go wrong, and if you don't preemptively plan for errors, your website can break or appear unresponsive to users.

To simulate a network error, scroll up to the previous code snippet and change the `fetch` URL to something random. After a refresh of your browser window, the page will remain a blank white screen, without giving the user any indication that the page has finished loading or that there was an error.

To fix this, we need to check for _something_ before Image component returns JSX. We'll call it: `error`.

```js
if (error) return <p>A network error was encountered.</p>

return (
	imageURL && (
		<>
			<h1>An image</h1>
			<img src={imageURL} alt={'placeholder text'} />
		</>
	)
)
```

To set this `error`, we'll add it to the component's state.

```js
const [imageURL, setImageURL] = useState(null)
const [error, setError] = useState(null)
```

And finally, to assign `error` a value when a request fails, we'll add a conditional to check the response status, and set it where our console.error line was.

```js
useEffect(() => {
	fetch('https://jsonplaceholder.typicode.com/photos', {
		mode: 'cors',
	})
		.then((response) => {
			if (response.status >= 400) {
				throw new Error('server error')
			}

			return response.json()
		})
		.then((response) => setImageURL(response[0].url))
		.catch((error) => setError(error))
}, [])
```

> Notice how we also handle errors in the `then` block? This is because the `fetch` request itself might not fail, but rather complete successfully and yield a response. However, the response received may not be what our app expected. To handle this case, we check the response status codes.

Now when a bad URL is passed or the API returns an unexpected response, the page will relay that information to the user.

<br>

### Loading State

In the same way we added an error value in state to check for errors, we can also add a loading value to check whether the request is resolved or not.

```js
const Image = () => {
	const [imageURL, setImageURL] = useState(null)
	const [error, setError] = useState(null)
	const [loading, setLoading] = useState(true)

	useEffect(() => {
		fetch('https://jsonplaceholder.typicode.com/photos', {
			mode: 'cors',
		})
			.then((response) => {
				if (response.status >= 400) {
					throw new Error('server error')
				}
				return response.json()
			})
			.then((response) => setImageURL(response[0].url))
			.catch((error) => setError(error))
			.finally(() => setLoading(false))
	}, [])

	if (loading) return <p>Loading...</p>

	if (error) return <p>A network error was encountered</p>

	return (
		<>
			<h1>An image</h1>
			<img src={imageURL} alt={'placeholder text'} />
		</>
	)
}
```

<br>

## Using custom hooks

We can separate out the fetching logic altogether into a custom hook. This will allow us to make the logic reusable and easily testable.

Recall in the Introduction to State lesson we said that a React hook is just a function that lets you use features of React (like states, effects etc) and that they follow a naming rule where they begin with `use` followed by a capital letter (e.g. `useState` or `useEffect`). If we tried to put a hook such as `useEffect` inside our own regular helper function like `getImageURL`, React would not be happy about this since it only wants hooks to be called in the top level of a component or another hook. Therefore, we can just turn our helper function into a custom hook by following the hook naming rule -- `useImageURL`.

Here's how we would do it for our example:

```js
import { useState, useEffect } from 'react'

const useImageURL = () => {
	const [imageURL, setImageURL] = useState(null)
	const [error, setError] = useState(null)
	const [loading, setLoading] = useState(true)

	useEffect(() => {
		fetch('https://jsonplaceholder.typicode.com/photos', {
			mode: 'cors',
		})
			.then((response) => {
				if (response >= 400) {
					throw new Error('server error')
				}
				return response.json()
			})
			.then((response) => setImageURL(response[0].url))
			.catch((error) => setError(error))
			.finally(() => setLoading(false))
	}, [])

	return { imageURL, error, loading }
}

const Image = () => {
	const { imageURL, error, loading } = useImageURL()

	if (loading) return <p>Loading...</p>

	if (error) return <p>A network error was encountered</p>

	return (
		<>
			<h1>An image</h1>
			<img src={imageURL} alt={'placeholder text'} />
		</>
	)
}
```

If we ever needed to fetch images in different components, instead of rewriting all of that fetching logic we could call `useImageURL`.

<br>

## Managing multiple fetch requests

In a full-scale web app, you're often going to be making more than one request, and you need to be careful with how you organize them. A common issue that new React developers face when their apps start making multiple requests is called a _waterfall of requests_. Let's look at an example:

[Code Sandbox Link](https://codesandbox.io/p/sandbox/github/TheOdinProject/react-examples/tree/main/fetching-data-example?embed=1&file=%2Fsrc%2Fmain.jsx)

We have two component making fetch requests: `Profile` and its child component `Bio`. The requests in `Profile` and `Bio` are both firing inside of their respective components. On the surface this looks like a well-organized separation of concerns, but in this case, it comes at a cost in performance.

Notice how `Bio` is taking an extra second to display? Their fetch requests should both take 1000ms to resolve so what's going on? In React, the component is not rendered until it is actually called. If JSX has conditional logic, the false branches will never render until they become true. `Bio` has to wait for the request inside of `Profile` to resolve before it starts rendering, which means the request inside `Bio` isn't sent.

If we remove the short-circuiting conditional that waits for `imageURL`, `Bio` would send a request immediately, but that would mean abandoning our loading screen. Instead of compromising on design, we can lift the request up the component tree and pass its response as a prop to `Bio`.

To see this in action, go back to that embedded CodeSandbox and comment out the current `Profile` and `Bio` components, and uncomment the currently commented ones.

Now we have both requests firing as soon as `Profile` renders. The request for `imageURL` resolves 2 seconds before the `bioText` request, and our div containing `<Bio />` renders. When `bioText` resolves, an update will be made in state which will trigger a rerender in `<Bio />`, adding that text description to the page.

> In all of the code examples above, we added an artificial `delay` with the `setTimeout` function. As you've likely guessed by now, this is to help you walk through the data fetching basics in the lesson. We recommend removing these `delay`s and playing around with the code examples to further cement the concepts.

<br>

## Data fetching libraries

We've only just begun to scratch the surface of data fetching on the frontend. Keeping your frontend data up-to-date with the server is a challenging task to accomplish. Managing "async"state becomes increasingly complex with each added feature.

You've already tasted the complexity of data fetching in this lesson. Each request has to have a _minimum_ of three states to achieve an optimal user experience: `data`, `loading`, and `error`. Although some libraries can help you with data fetching and more, it is highly recommended to use vanilla React data fetching for all the projects in this course. The lessons you will learn while doing so will be invaluable.

<br>

## Knowledge Check

- **How can you fetch data from an API in React?**

<br>

- **Why should you manually throw errors in fetch requests?**

<br>

- **How can you avoid waterfalling requests?**

<hr>
<br>
<br>

# [Modern API data-fetching methods in React](https://blog.logrocket.com/modern-api-data-fetching-methods-react/)

Over the years, how we fetch data into React applications have evolved. For developers who aim to be ahead of the curve, understanding how fetching data works in the current dispensation is essential.

In this guide, we'll explore the modern React data-fetching methods. We'll cover what you need to know about each method, edge cases, and benefits so that you can decide the right solution for your project.

You can check out the [project code in this GitHub repo](https://github.com/Ibaslogic/data-fetching-methods) to see the code examples we'll explore in this tutorial. You can see [the live demo here](https://data-fetching-methods.vercel.app/posts/8) as well. Let's get started.

<br>

## Understanding API: A quick overview

API, or Application Programming Interface, is a protocol or contract that allows one application to communicate with another. In other words, APIs act as intermediaries, enabling the exchange of information between different systems.

<br>

## Why APIs?

Let's think of an application where a section displays the daily weather forecast of the present city. While building this type of app, we can create our backend to handle the weather data logic or we can simply make our app communicate with a third-party system that has all the weather information so we only need to render the data.

Either way, the app must communicate with the backend. This communication is possible via an API, and in this case, a web API, which allows communication over the internet, typically using HTTP (HyperText Transfer Protocol).

With the API, we don't need to create everything from scratch, which will simplify our process. It allows access to where the data is located so we can use it in our app. The two common styles for designing web APIs are REST and GraphQL. While this guide focuses on data fetching from the REST API, the fetching strategies are similar for both.

<br>

## What are API calls in React?

When a React app (client) needs to access resources from the backend (server), it makes the request through the API and expects a response. Each request and response cycle constitutes an API call.

To initiate API calls either to retrieve information or perform other operations, we will use HTTP methods like GET, POST, PUT, and DELETE.

<br>

## Fetching data from an API in a React app

While data fetching can be simple, handling the data upon returning to the client can be complicated.

Before we fetch data, we need to consider where the data will live, how we'll manage the loading state to improve the user experience, and also the error state should anything go wrong. In addition, we need to consider adding optimizations like caching, request duplication, and preventing race conditions.

Now that we have covered the basics, we can get started with the first fetching method.

<br>

## API calls with `fetch()` in a `useEffect` Hook

The Fetch API, through the `fetch()` method, allows us to make an HTTP request to the backend. With this method, we can perform different types of operations using HTTP methods like the `GET` method to request data from an endpoint, `POST` to send data to an endpoint, and more.

`fetch()` requires the URL of the source we want to fetch and an optional parameter:

```js
fetch(url, options)
```

We can also specify the HTTP method in the optional parameter. For the `GET` method, we have the following:

```js
fetch(url, {
	method: 'GET', // other options: POST, PUT, DELETE, etc.
})
```

Or, we can simply ignore the optional parameter because `GET` is the default:

```js
fetch(url)
```

For the `POST` method, we will stringify the object we want to pass to the request body and also explicitly set the `Content-Type` in the headers like so:

```js
fetch(url, {
	method: 'POST',
	headers: {
		'Content-Type': 'application/json',
	},
	body: JSON.stringify({}),
})
```

As mentioned earlier, we will fetch data from a REST API. We could use any API, but here we will use a free online API called JSONPlaceholder to fetch a list of posts into our application; here is a list of the resources we can request.

By applying what we've learned so far, a typical `fetch()` request with `fetch()` looks like the following:

```js
import { useEffect, useState } from 'react'

const FetchGetRequest = () => {
	const [data, setData] = useState(null)
	const [loading, setLoading] = useState(true)
	const [error, setError] = useState(null)

	useEffect(() => {
		const fetchDataForPosts = async () => {
			try {
				const response = await fetch(
					`https://jsonplaceholder.typicode.com/posts?_limit=8`
				)

				if (!response.ok) {
					throw new Error(`HTTP error: Status ${response.status}`)
				}
				let postsData = await response.json()
				setData(postsData)
				setError(null)
			} catch (err) {
				setError(err.message)
				setData(null)
			} finally {
				setLoading(false)
			}
		}

		fetchDataForPosts()
	}, [])

	return <div></div>
}

export default FetchGetRequest
```

In the code, we are using the `fetch()` function to request post data from the resource endpoint as seen in the `useEffect` hook.

In React, we avoid performing side effects like data fetching directly within the component body to avoid inconsistencies. Instead, we isolate them from the rendering logic using the `useEffect` Hook as we did above.

The `fetch` function returns a promise that can either be resolved or rejected. Because this is an asynchronous operation, we often use `async/await` with `try/catch/finally` statement to catch errors and manage the loading state. We may also use the pure promise with `.then`, `.catch` and `.finally` statements.

If the promise resolves, we handle the response within the try block and then update the data while resetting the error state. Initially, the returned data is a `Response` object, which is not the actual format that we need. We must resolve the `Response` object to JSON format using the `json()` method. This also returns a promise and so we wait for it until the promise settles with the actual data.

In case the promise is rejected, we handle the error within the catch block and update the error state while also resetting the data state, which helps prevent inconsistencies for temporary server failure.

Be aware that the promise returned from the `fetch()` function only rejects on a network failure; it won't reject if we hit a wrong or non-existing endpoint like `.../postssss`. For that reason, we've used the response object to check for the HTTP status and throw a custom error for a "404 Not Found". This way, the catch block can detect the error and use our custom message whenever we hit a "404 Not Found."

<br>

## Rendering the post data with `fetch()`

After updating our state variables with `setData`, `setError`, and `setLoading` within the `try/catch/finally` block, we can now render the UI like so:

```js
import { NavLink } from 'react-router-dom'

const FetchGetRequest = () => {
	// ...

	return (
		<div className='flex'>
			<div className='w-52 sm:w-80 flex justify-center items-center'>
				{loading && <div className='text-xl font-medium'>Loading posts...</div>}
				{error && <div className='text-red-700'>{error}</div>}

				<ul>
					{data &&
						data.map(({ id, title }) => (
							<li
								key={id}
								className='border-b border-gray-100 text-sm sm:text-base'
							>
								<NavLink
									className={({ isActive }) => {
										const baseClasses = 'p-4 block hover:bg-gray-100'
										return isActive ? `${baseClasses} bg-gray-100` : baseClasses
									}}
									to={`/posts/${id}`}
								>
									{title}
								</NavLink>
							</li>
						))}
				</ul>
			</div>

			<div className='bg-gray-100 flex-1 p-4 min-h-[550px]'>
				Single post here....
			</div>
		</div>
	)
}

export default FetchGetRequest
```

We grabbed the post data state, looped through the list, and rendered the post title. See the demo below. We've also added styles to improve the visuals:

![](images/1.gif)

<br>

## Extract the fetching logic

Let's improve the code readability by extracting the fetching logic into a separate file:

```js
export const getRequestWithNativeFetch = async (url) => {
	const response = await fetch(url)

	if (!response.ok) {
		throw new Error(`HTTP error: Status ${response.status}`)
	}

	return response.json()
}
```

The `useEffect` now looks like this:

```js
useEffect(() => {
	const fetchDataForPosts = async () => {
		try {
			const postsData = await getRequestWithNativeFetch(
				'https://jsonplaceholder.typicode.com/posts?_limit=8'
			)
		} catch (err) {
			setError(err.message)
			setData(null)
		} finally {
			setLoading(false)
		}
	}

	fetchDataForPosts()
}, [])
```
