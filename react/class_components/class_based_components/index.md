# [Class Based Components](https://www.theodinproject.com/lessons/node-path-react-new-class-based-components)

## Introduction

All the components so far have been functional in style and syntax. This is common now, but you will see a different `class` based syntax too. In this lesson, we explore how a class-based component is written and how concepts like props and state are used in one.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Learn the structure of a class component and how they are written.

- How to use props and state in class components

- Highlight the uses of `this` in class components

<br>

## Historical React component patterns

In your previous lessons, you have already been introduced to functional components, and the basic patterns in which components get written nowadays. However, React components did not look this way when React was introduced.

If you look into any older React codebase, you'll notice a lot of classes. These are known as class-based components. Prior to February 2019, functional components were also called state-less, as there was no way to manage state in them. This was changed when hooks were introduced, leading to less verbose and 'neater' components.

In your career, chances are, you will be dealing with legacy code, so there will be days where you would be dealing with class components. Let's peek into the intricacies of a class-based component, and how they work.

<br>

## Building a class component

As we already know about functional components, let us build a class-based component from a functional one. Usually, you will want to divide the contents of a component, like the one we use, into smaller, reusable components, but for the purpose of this exercise, we stick to one component. Below, we have a sample functional component:

```js
import { useState } from 'react'

const FunctionalInput = ({ name }) => {
	const [todos, setTodos] = useState(['Just some demo tasks', 'As an example'])
	const [inputVal, setInputVal] = useState('')

	const handleInputChange = (e) => {
		setInputVal(e.target.value)
	}

	const handleSubmit = (e) => {
		e.preventDefault()
		setTodos((prevTodos) => [...prevTodos, inputVal])
		setInputVal('')
	}

	return (
		<section>
			<h3>{name}</h3>
			<form onSubmit={handleSubmit}>
				<label htmlFor='task-entry'>Enter a task: </label>
				<input
					type='text'
					id='task-entry'
					name='task-entry'
					value={inputValue}
					onChange={handleInputChange}
				/>
				<button type='submit'>Submit</button>
			</form>
			<h4>All the tasks!</h4>
			<ul>
				{todos.map((todo) => (
					<li key={todo}>todo</li>
				))}
			</ul>
		</section>
	)
}

export default FunctionalInput
```

That was a solid chunk of code. Take a while, sip some water and read it a couple of times.

<br>

### The start of a class-based component

Now, let's try to recreate is as a class-based component. The first thing it should have is, _drumroll_, a class! But it cannot be just another class, it will need to have certain properties that qualifies it as a React component. React provides us with all those properties on a class called `Component`, and we can write our components by extending the given class, as shown below:

```js
import { Component } from 'react'

class ClassInput extends Component {
	// Some code goes here
}

/* 
  This can also be written as:

  import React from 'react'
  class ClassInput extends React.Component {}
  export default ClassInput

  instead of destructuring the `Component` during import
*/

export default ClassInput
```

<br>

### The use of a constructor and props

A class is generally incomplete without a constructor, so let's add one.

The props passed into this component are passed to the class's `constructor`. This, along with the `super` method, allows you to use the props in the context of `this`, which, in _this_ case, refers to the component. If you're really curious about what `super` actually does, check out the [MDN docs on the `super` keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super).

If your component doesn't have any props, it is fine to leave the `constructor` and the `super` with no arguments.

```js
import { Component } from 'react'

class ClassInput extends Component {
	constructor(props) {
		super(props)
	}

	// Some more code goes here
}

export default ClassInput
```

<br>

### How you can render JSX

Now that the props can be accessed inside of the class component, the next issue is to find a way to render the JSX.

Well, you can do that by returning your JSX from a `render` method! You can use the props that you declared in the constructor too!

```js
import { Component } from 'react'

class ClassInput extends Component {
	constructor(props) {
		super(props)
	}
	// Some more code goes here

	render() {
		return (
			<section>
				<h3>{this.props.name}</h3>
				{/* The input field to enter Todos */}
				<form>
					<label htmlFor='task-entry'>Enter a task: </label>
					<input id='task-entry' type='text' name='task-entry' />
					<button type='submit'>Submit</button>
				</form>
				<h4>All the tasks!</h4>
				{/* The list of all the Todos, displayed */}
				<ul></ul>
			</section>
		)
	}
}

export default ClassInput
```

Notice how the props get provided by `this`, unlike the functional component that we saw, initially?

<br>

### How to use state and manage context

Next comes the state. In a class-based component, the state gets initialized as a part of the constructor.

```js
import { Component } from 'react'

class ClassInput extends Component {
	constructor(props) {
		super(props)

		this.state = {
			todos: [],
			inputVal: '',
		}
	}
	// Some more code goes here

	render() {
		return (
			<section>
				<h3>{this.props.name}</h3>
				<form>
					<label htmlFor='task-entry'>Enter a task: </label>
					<input type='text' id='task-entry' name='task-entry' />
					<button type='submit'>Submit</button>
				</form>
				<h4>All the tasks!</h4>
				<ul></ul>
			</section>
		)
	}
}

export default ClassInput
```

The pre-defined `setState` method can be used to set it again! Remember, state must not be mutated, so a new state must be set, every time.

Now, it is time to finish it off by adding all the functionality! It is nearly the same, except for a single difference. Whenever a method is declared, you must `bind` the `this` of the method to that of the class in order to work with it, as by default, the methods in a class are not bound to it. Usually, you do this inside the constructor and not at runtime [in the render method].

```js
import { Component } from 'react'

class ClassInput extends Component {
  constructor(props) {
    super(props)

    this.state = {
      todos: [],
      inputVal: ''
    }

    this.handleInputChange = this.handleInputChange.bind(this)
    this.handleSubmit = this.handleSubmit.bind(this)
  }

  handleInputChange(e) {
    this.setState((state) => ({
      ...state,
      inputVal: e.target.value
    }))
  }

  handleSubmit(e) {
    e.preventDefault()
    this.setState((state) => ({
      todos: state.todos.concat(state.inputVal)
      inputVal: ''
    }))
  }

  render() {
    return (
      <section>
        <h3>{this.props.name}</h3>
        <form onSubmit={this.handleSubmit}>
          <label htmlFor='task-entry'>Enter a task: </label>
          <input id='task-entry' name='task-entry' type='text' value={this.state.inputVal} onChange={this.handleInputChange} />
          <button type='submit'>Submit</button>
        </form>
        <h4>All the tasks!</h4>
        <ul>
          {this.state.todos.map((todo) => (
            <li key={todo}>{todo}</li>
          ))}
        </ul>
      </section>
    )
  }
}

export default ClassInput
```

And there we go, we have successfully made our first class-based component, as easy as that!

<br>

## Knowledge Check

- **How do props get used in a class-based components?**

The props passed into the class-based components are passed to its `constructor`. This, along with the `super` method, allows you to use the props in the context of `this`, which, in this case, refers to the component.

<br>

- **How does JSX get displayed?**

JSX is displayed by returning it in the render method.

<br>

- **How do we deal with state in a class-based component?**

State is stored on `this.state` which is initialized in the constructor method. You pass on the entire new state to `this.setState` in order to update the state.

<br>

- **How do you restore the context of `this` in a method?**

Whenever a method is declared, you must `bind` the `this` of the method to that of the class in order to work with it, as by default, the methods in a class are not bound to it. Usually, you do this inside the constructor and not at runtime.
