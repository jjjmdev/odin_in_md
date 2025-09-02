[link](https://blog.logrocket.com/validate-react-props-proptypes/)

## Custom validators for type checking React props

Usually, you need to define some custom validation logic for component props, for example, to ensure that a prop is passed a valid email address. `prop-types` allows you to define custom validation functions that you can use for type checking props.

<br>

### Basic custom validators

The custom validation function takes three arguments:

- `props`: An object containing all the props passed to the component

- `propName`: The name of the prop to be validated

- `componentName`: The name of the component

If the validation fails, it should return an `Error` object. The error should not be thrown. Additionally, you shouldn't use `console.warn` inside the custom validation function:

```js
const isEmail = function (props, propName, componentName) {
  const regex =
    /^((([^<>()[]\.,;:s@"]+(.[^<>()[]\.,;:s@"]+)*)|(".+"))@(([[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}])|(([a-zA-Z-0-9]+.)+[a-zA-Z]{2,})))?$/

  if (!regex.test(props[propName])) {
    return new Error(`Invalid prop `${propName}` passed to `${componentName}`. Expected a valid email address.`)
  }
}

Component.propTypes = {
  email: isEmail,
  fullname: PropTypes.string,
  date: PropTypes.instanceOf(Date)
}
```

![](images/4.png)

You can also use custom validation functions with `PropTypes.oneOfType`. The example below uses the `isEmail` custom validation function from the previous code snippet:

```js
Component.propTypes = {
	email: PropTypes.oneOfType([
		isEmail,
		PropTypes.shape({
			address: isEmail,
		}),
	]),
}
```

The component will be valid in both of these scenarioss:

```jsx
<Component email="glad@me.com" />
<Component email={{address: 'glad@me.com'}} />
```

<br>

### Custom validators and collections

You can also use custom validation functions with `PropTypes.arrayOf` and `PropTypes.objectOf`. When used this way, the custom validation function is called for each key in the array or object.

The custom validation function takes five arguments instead of three:

- `propValue`: The array or object itself

- `key`: The key of the current item in the iteration

- `componentName`: The name of the component

- `location`: The location of the validated data, usually `prop`

- `propFullName`: The fully resolved name of the current item being validated. For an array, this will be `array[index]`; for an object, it will be `object.key`.

Below is a modified version of the `isEmail` custom validation function for use with collection types:

```js
const isEmail = function (
  propValue,
  key,
  componentName,
  location,
  propFullName
) {
  const regex =
    /^((([^<>()[]\.,;:s@"]+(.[^<>()[]\.,;:s@"]+)*)|(".+"))@(([[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}])|(([a-zA-Z-0-9]+.)+[a-zA-Z]{2,})))?$/

  if (!regex.test(propValue[key])) {
    return new Error(`Invalid prop `${propFullName}` passed to `${componentName}`. Expected a valid email address.`)
  }
}

Component.propTypes = {
  emails: PropTypes.arrayOf(isEmail)
}
```

<br>

### All-purpose custom validators

Taking everything we've learned about custom validation functions into account, let's go ahead and create all-purpose custom validators that we can use as standalone validators as well as with collection types.

We can make the `isEmail` custom validation function an all-purpose validator with just a slight modification. We'll add a `prop` variable that returns either the `propFullName` or the `key`. With this, our custom validator can either be used on its own or with collections:

```js
const isEmail = function (
  propValue,
  key,
  componentName,
  location,
  propFullName
) {
  // Get the resolved prop name based on the validator usage
  const prop = location && propFullName ? propFullName : key

  const regex =
    /^((([^<>()[]\.,;:s@"]+(.[^<>()[]\.,;:s@"]+)*)|(".+"))@(([[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}])|(([a-zA-Z-0-9]+.)+[a-zA-Z]{2,})))?$/

  if (!regex.test(propValue[key])) {
    return new Error(`Invalid prop `${prop}` passed to `${componentName}`. Expected a valid email address.`)
  }
}

Component.propTypes = {
  email: PropTypes.oneOfType([
    isEmail,
    PropTypes.shape({
      address: isEmail
    })
  ]),
  emais: PropTypes.arrayOf(isEmail)
}
```

<hr>
<br>
<br>

[link](https://blog.logrocket.com/validate-react-props-proptypes/)

### All-purpose custom validators

Taking everything we've learned about custom validation functions into account, let's go ahead and create all-purpose custom validators that we can use as standalone validators as well as with collection types.

We can make the `isEmail` custom validation function an all-purpose validator with just a slight modification. We'll add a `prop` variable that returns either the `propFullName` or the `key`. With this, our custom validator can either be used on its own or with collections:

```js
const isEmail = function (
	propValue,
	key,
	componentName,
	location,
	propFullName
) {
	// Get the resolved prop name based on the validator usage
	const prop = location && propFullName ? propFullName : key

	const regex =
		/^((([^<>()[]\.,;:s@"]+(.[^<>()[]\.,;:s@"]+)*)|(".+"))@(([[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}])|(([a-zA-Z-0-9]+.)+[a-zA-Z]{2,})))?$/

  if (!regex.test(propValue[key])) {
    return new Error(`Invalid prop `${prop}` passed to `${componentName}`. Expected a valid email address.`)
  }
}

Component.propTypes = {
  email: PropTypes.oneOfType([
    isEmail,
    PropTypes.shape({
      address: isEmail
    })
  ]),
  emais: PropTypes.arrayOf(isEmail)
}
```

<br>

### Validating `PercentageStat` in React

The following code snippet adds prop types to the `PercentageStat` component that we reviewed at the beginning of this tutorial:

```js
import React from 'react'
import PropTypes from 'prop-types'

// The PercentageStat Component
function PercentageStat({ label, score = 0, total = Math.max(1, score) }) {
	return (
		<div>
			<h6>{label}</h6>
			<span>{Math.round((score / total) * 100)}%</span>
		</div>
	)
}

// Checks if a value is numeric
// Either a finite number or a numeric string
function isNumeric(value) {
	const regex = /^(\+|-)?((\d*\.?\d+)|(\d+\.?\d*))$/
	return (
		Number.isFinite(value) || (typeof value === 'string' && regex.test(value))
	)
}

// Checks if value is non-zero
// Value is first converted to a number
function isNonZero(value) {
	return +value !== 0
}

// Takes test functions as arguments and returns a custom validation function
// Each function passed in as argument is expected to take a value argument
// expected to accept a value and return a Boolean if it passes the validation.
// All tests must pass for the custom validator to be marked as passed.
function validatedType(...validators) {
	return function (props, propName, componentName) {
		const value = props[propName]

		const valid = validators.every((validator) => {
			if (typeof validator === 'function') {
				const result = validator(value)
				return typeof result === 'boolean' && result
			}

			return false
		})

		if (!valid) {
			return new Error(
				`Invalid prop \`${propName}\` passed to \`${componentName}\`. Validation failed.`
			)
		}
	}
}

// Set the propTypes for the component
PercentageStat.propTypes = {
	label: PropTypes.string.isRequired,
	score: validatedType(isNumeric),
	total: validatedType(isNumeric, isNonZero),
}
```

<hr>
<br>
<br>

[Active Link Styling using React-Router](https://reactrouter.com/6.28.0/start/tutorial#active-link-styling)

- Automatically add className 'active' or 'pending' for Nav Link to indicate which one is active or which one is pending

<br>

[Pending UI using React-Router](https://reactrouter.com/6.28.0/start/tutorial#global-pending-ui)

- Adds `navigation.state` that can be `idle || submitting || loading`

<br>

[Adding spinner when the page is loading](https://reactrouter.com/6.28.0/start/tutorial#adding-search-spinner)

<br>

[Submitting form (mutating) without navigation](https://reactrouter.com/6.28.0/start/tutorial#mutations-without-navigation)

<br>

[Optimistic UI](https://reactrouter.com/6.28.0/start/tutorial#optimistic-ui)

Updating the UI with the submitted formData before it even reflects, but at the same time have the actual data go back if it fails
