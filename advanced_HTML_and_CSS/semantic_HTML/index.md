# [Semantic HTML](https://www.theodinproject.com/lessons/node-path-advanced-html-and-css-semantic-html)

## Introduction

As useful as `<div>` and `<span>` elements can be as generic containers, they're not always the most a11y friendly elements to use. While it may be tempting or easier to just use them for everything, from containers to interactive areas, you should not only check whether there is a more appropriate element to use in certain situations, but also whether you're using an element correctly.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Explain why semantic HTML is important for accessibility

- Name the seven HTML elements that define landmarks on a page.

<br>

## The importance of semantics

In terms of web accessibility, using semantic HTML is important because it provides meaning and context. Some elements have a _semantic meaning_, but don't really provide any _context_ when announced by assistive technologies, such as the `<p>` element. Then there are elements that have a semantic meaning _and_ are announced with some sort of context to help users perceive or operate them, like a `<button>`.

The `<div>` and `<span>` elements, most likely two of the more common elements you use, are semantically neutral. That is, they themselves have no semantic meaning and provide no context on their own to assistive technologies, which can make it more difficult for users of such technologies to perceive, operate, and understand them. Don't let this lack of semantics and context make you feel like you can never use a `<div>` or `<span>` ever again, though. They still have their uses as generic containers, such as layouts or for generic text.

Okay, let's look at an actual example to help better understand this whole semantics and context thing. Think of any project you may have completed so far that required a user to click on something: Rock, Paper, and Scissors; Calculator; Tic-Tac-Toe. If you used `<div>` or `<span>` elements for any clickable areas, things most likely worked as intended for you. For example, perhaps you had something similar to the HTML below for your Rock, Paper, Scissors UI back in Foundations:

```html
<!-- These are buttons... right? -->
<div class="button-container">
	<div class="rock">Rock</div>
	<div class="paper">Paper</div>
	<div class="scissors">Scissors</div>
</div>
```

A sighted user would most likely have no trouble playing the game if the elements looked like something to interact with. A screen reader user, however, would have no idea what any of these elements mean. The screen reader would announce the text contents of the element ("Rock", "Paper", or "Scissors"), and the user might think it's just plain text on the page and move on. There's no context to tell the user that they're supposed to, or that they even _can_, interact with these elements.

This issue can be easily fixed by using semantic HTML:

```html
<!-- Okay, these are *definitely* buttons -->
<div class="button-container">
	<button class="rock">Rock</button>
	<button class="paper">Paper</button>
	<button class="scissors">Scissors</button>
</div>
```

Because the `<button>` element has a semantic meaning and provides context, a screen reader would announce the text content as well as the role of the element: "Rock, button".

<br>

### Using semantic HTML correctly

When it comes to using semantic HTML correctly, you want to think about what your intent for users is and what context you want (or need) to provide to them. This can vary depending on the situation, but there are some things you should absolutely be checking moving forward:

- If a user is meant to click something, whether it's an actual button or not, you will usually want to use a `<button>` element. This will let the user know that they can interact with the element by clicking on it.

- If you want to provide some sort of tabular data to a user, use a `<table>` element along with the elements related to it. This will allow a user to more easily navigate and understand the data being presented.

- When you use an input element, you should always create a relationship between it and a `<label>` element. A `<label>` provides context for what an input actually means to assistive technologies, announcing the label contents each time the input is announced. Not only that, but a proper `<label>` increases the clickable area of the input itself, which is useful for users who have trouble clicking on smaller items. There are two ways you can create this relationship:

```html
<!-- Useful for when you need the input itself to have an ID -->
<label for="name">Name</label>
<input type="text" id="name" />

<!-- Look, no ID! -->
<label>
	Name
	<input type="text" />
</label>
```

- Continuing with inputs, you should always use the `type` that makes the most sense for its intended use. `type="text"` makes more sense for a name or address field, while `type="email"` or `type="tel"` would of course make more sense for an e-mail or telephone field, respectively. For certain devices, using the correct `type` may show only the required or additional characters on the keyboard. A `type="tel"` input, for example, might make it much easier for users to fill out their phone numbers by providing larger, numerical-only keys on mobile or tablet devices.

- When you want to present a list of some sort to a user, you should use the appropriate list element (`<ol>`, `<ul>`, or `<dl>`) and their related list item elements. This will not only let the user know when they are entering or exiting a list, but also how many items are in the list.

<br>

## Headings and landmarks

Headings are the `<h1>` through `<h6>` elements, and like the name implies, these elements act as headings to sections of a page. Landmarks, on the other hand, are HTML elements that act as regions of a page. There are seven native HTML elements that define these landmark regions:

- `<aside>`

- `<footer>`

- `<form>`

- `<header>`

- `<main>`

- `<nav>`

- `<section>`

As an example, consider the following image which shows how this lesson in particular uses semantic HTML for the different areas in the page. If you want to examine the page in more detail, feel free to use the developer tools to do so.

![](images/1.png)

By properly using landmarks and headings, you provide users of assistive technologies a more operable and understandable page: not only can screen reader users navigate a page via landmarks and headings by using navigation keyboard commands (or opening a menu in their screen reader), but these elements also have their roles announced to provide additional context.

If you were to use only `<div>` elements to act as these landmarks and headings, maybe adding in some CSS to visually style them, then a screen reader user would have to go through the entire page just to get to a specific section, and they may not be able to actually tell what is a heading or a landmark on the page.

<br>

## Knowledge check

- ##### Why is semantic HTML important for accessibility?

Using semantic HTML is important because it provides meaning and context. They are announced by assistive technologies with some sort of context to help users perceive or operate or understand them.

<br>

- ##### What are the seven HTML elements that define landmarks on a page?

The seven HTML elements that define landmarks on a page are as follows: `aside`, `main`, `nav`, `footer`, `form`, `heading`, and `section`.

<hr>
<br>
<br>

# [How screen readers navigate data tables](https://tink.uk/how-screen-readers-navigate-data-tables/)

When a table is created using the appropriate HTML elements (or ARIA roles) screen readers can inform users about the characteristics of the table, and users have access to keyboard commands specifically for navigating tabular content.

For the purpose of this post I'm going to use NVDA. Jaws uses the same keyboard commands in this situation, which is useful because between them they represent more than 80% of the screen reader market on desktop/laptop devices. Check the documentation for VoiceOver and Narrator to find the corresponding keyboard commands for those screen readers.

One more thing before we get started; there is a difference between keyboard and screen reader navigation. Although most screen reader users use a keyboard not a mouse, they are not restricted to the same limited set of keyboard commands as other keyboard users. It also means that keyboard focus and screen reader focus are not the same thing.

Contrary to what you might have heard, you do not need to make each cell of a table focusable with a keyboard to aid navigation. If the cell contains a focusable and interactive element that's OK, but if it contains non-interactive content is it likely that you will make keyboard users work much harder to navigate the table than you intended.

<br>

## Moving to a table

Let's use the following table as our working example:

```html
<table>
	<caption>
		Average daily tea and coffee consumption
	</caption>

	<tr>
		<th>Person</th>
		<th>Coffee</th>
		<th>Tea</th>
	</tr>

	<tr>
		<th>Njoki</th>
		<td>5 cups</td>
		<td>0 cups</td>
	</tr>

	<tr>
		<th>Iesha</th>
		<td>1 cup</td>
		<td>2 cups</td>
	</tr>

	<tr>
		<th>Leonie</th>
		<td>0 cups</td>
		<td>25 cups</td>
	</tr>
</table>
```

Press `t` to move screen reader focus to the table and NVDA will say:

> _Average daily tea and coffee consumption_
>
> _Table with 3 columns and 4 rows_
>
> _Average daily tea and coffee consumption caption_

NVDA starts by announcing the table's accessible name, then that there is a table with 3 columns and 4 rows, before repeating the accessible name again but this time indicating it is the table's caption.

All of this information comes from the browser; the table's accessible name is taken from the `<caption>` element, the implicit role of the `<table>` element is "table" (which is how the screen reader knows what it is), and the browser tells the screen reader how many rows and columns there are based on the number of `<td>` and `<tr>` elements.

The repetition of the table caption makes NVDA a little verbose, but it is an example of a common phenomenon -- screen readers often do the same thing in slightly different ways. Jaws, for example, announces this when you press the `t` key:

> _Table with 3 columns and 4 rows_
>
> _Average daily tea and coffee consumption_
>
> _Column 1, row 1_
>
> _Person_

Jaws does not repeat the caption, but it does not indicate that the name of the table is a caption either. It also takes the additional step of moving screen reader focus to the first cell in the table and announcing its coordinates and content, where NVDA only moves screen reader focus to the table (not into it).

These differences are entirely normal and nothing to worry about. The important question to ask when you're testing with any screen reader is: will someone who uses this screen reader know what kind of content they're dealing with?

Whether you're using NVDA or Jaws, you'll know that there is a table, the table's dimensions, and something about the table content. In other words, you'll have the same information someone sighted might discover by glancing at it.

<br>

## Navigating table content

Use the `down arroy` key to move NVDA's focus into the table and NVDA will say:

> _Row 1, column 1_
>
> _Person_

Now the screen reader focus is in the first cell of the table, the next step is to explore the table and orientate yourself so you know what data the table contains.

Use the keyboard command `control alt + right arrow` to move on cell to the right, and NVDA will say:

> _Column 2_
>
> _Coffee_

Then repeat the same keyboard command until NVDA says:

> _Edge of table_

Then use `control alt + left arrow` to reverse direction until NVDA says:

> _Edge of table_

Now use `control alt + down arrow` to move one cell down, and NVDA will say:

> _Row 2_
>
> _Njoki_

Repeat the same keyboard command until NVDA says:

> _Edge of table_

Then use `control alt + up arrow` to reverse direction until NVDA tells you you're at the edge of the table again.

These four keyboard commands let you move left/right through row and up/down through columns, and with them you have the basic method of navigating data tables with NVDA (and Jaws).

<br>

## Finding specific information

Let's say you want to find out how much coffee Njoki drinks. Use `control alt + down arrow` until NVDA says:

> _Row 2_
>
> _Njoki_

Then use `control alt + right arrow` and NVDA will tell you:

> _Coffee_
>
> _Column 2_
>
> _5 cups_

Even though the screen reader is focused on the `td` element that represents the cell containing the number of cups, not the `th` element that represents the column header, the screen reader uses the information it got from the browser to create an association between the two. The screen reader counts on you remembering which row you're in, and just announces the column header as well as the cell content as you move horizontally across the row.

Now you might want to know how many cups of coffee Iesha drinks. Use `control alt + down arrow` to move down one cell and NVDA will say:

> _Eisha_
>
> _Row 3_
>
> _1 cup_

This time the screen reader associates the `th` element that is the row header with the contents of the `td` it is focused on, and speaks both pieces of information. As before, the screen reader counts on you remembering which column you're in, and just announces the row header as you move vertically through the column.

This ability to navigate the table using these commands is entirely dependent on the proper HTML (or equivalent ARIA roles) being used; especially the `th` elements that act as row and column headers.

<hr>
<br>
<br>

# Video Links

- [How screen readers navigate data tables](https://www.youtube.com/watch?v=X1KR4u94cho)

- [Why headings and landmarks are so important -- A11ycasts #18](https://www.youtube.com/watch?v=vAAzdi1xuUY&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=20)
