# [WAI-ARIA](https://www.theodinproject.com/lessons/node-path-advanced-html-and-css-wai-aria)

## Introduction

In the previous lessons, you learned several ways to make websites more accessible. Those lessons, however, were just the tip of the accessible iceberg. WAI-ARIA introduces attributes that can help make websites even more accessible by modifying the semantics and context of elements, which can give you greater control over how those elements are perceived by assistive technologies. Because this subject can get so complicated, we're only going to cover two attributes that you can get _a lot_ of use from.

<br>

## Lesson Overview

This section contains a general overview of topics that you will learn in this lesson.

- Know the purpose of WAI-ARIA.

- Know what ARIA can't do.

- Understand the five rules of ARIA use.

- Understand what the accessibility tree is.

- Understand the three ARIA attribute that can add labels to elements.

- Understand what the `aria-hidden` attribute does.

<br>

## What is WAI-ARIA?

WAI-ARIA stands for - _deep breath_ - the Web Accessibility Initiative's Accessible Rich Internet Applications specification. The purpose of WAI-ARIA (often referred to as just ARIA) is to define a way to make web content more accessible when native HTML is unable to do so. Think of ARIA as something that fills in the accessible gaps left by native HTML.

It's important to note that ARIA can only modify the semantics or context of an element. ARIA _can't_:

- modify an element's appearance,

- modify an element's behavior,

- add focusability, or

- add keyboard event handling.

When you use ARIA, you will usually have to take additional steps to add in any missing semantics or functionality. Remember the Keyboard Navigation lesson and how we had to add in functionality to `<div>` "buttons"?

<br>

### The five rules of ARIA

ARIA can be extremely powerful when used correctly, but it can be equally as dangerous when used incorrectly. Because of this, you should keep in mind that **no ARIA is better than bad ARIA**, even when you have the best intentions. The WCAG has something called "The five rules of ARIA," which as you may have guessed are rules you should follow when using ARIA. Although we don't cover all of these terms mentioned below, it's still important to understand the rules themselves, especially if you decide to dive deeper into ARIA on your own.

1. Always use native HTML elements and attribute over ARIA when possible.

2. Never change native semantics, unless you have no other choice.

3. All interactive ARIA controls must be usable with a keyboard.

4. Never use `role="presentation"` or `aria-hidden="true"` on focusable elements.

5. All interactive elements must have an accessible name.

<br>

## The accessibility tree

Before we get into a couple of the ARIA attributes available to us, it's important to know some basics of what the accessibility tree is, as it will help you understand just what those attributes are actually doing.

The accessibility tree is based on the DOM, something you should be very with by now. While the DOM represents nodes and objects that make up a web page, the accessibility tree contains only the accessibility related information that will be used by assistive technologies. The way ARIA works is by modifying properties of the objects that make up this accessibility tree. For this lesson, we're only going to focus on two of these properties:

- **Name:** Also known as the "accessible name", this is what assistive technologies announce to a user and what separates elements of the same type from one another. The name may be set by one or more native labels, including the text contents of an element, the `<label>` element, or the `alt` attribute, to name a few.

- **Description:** This is what assistive technologies announce in addition to its accessible name.

<br>

## ARIA labels

ARIA labels help users of assistive technologies better understand the content on a web page by overriding native labels or providing additional descriptive text. Unlike the `<label>` element, ARIA labels aren't limited to being used on only a select few elements, though they still have their own limitations.

You remember being warned against using the `id` attribute earlier in the curriculum. To briefly recap, normally you want to avoid overusing `id` attributes or even using it when it isn't necessary (which more often than not, it isn't, and you should stick with using classes). There are several ARIA attributes, however, that actually _require_ another element to have an `id`.

When using such ARIA attributes, you would provide an `id` to one element, and you would then pass in that `id` value as another element's ARIA attribute value. This creates a link between the elements, similar to how a `<label>` element's `<for>` attribute creates a link to an input's `id`. Of the three types of ARIA labels mentioned below, `aria-labelledby` and `aria-describedby` are ARIA attributes that require another element to have an `id`.

<br>

### `aria-label`

The `aria-label` attribute overrides any native label of an element and modifies its name property in the accessibility tree. It is best used when an element doesn't already have a native label. When added, the string value of the `aria-label` attribute becomes the element's accessible name. **However**, [`aria-label` does not have any effect on some HTML elements](https://github.com/w3c/aria/issues/756), such as `<div>` or a `<span>`.

A common use for `aria-label` can be found in the "close" buttons of menus or modals:

```html
<button type="button" arial-label="Close menu">X</button>
```

Instead of a screen reader announcing, "X, button", which makes little sense to the user, it would announce, "Close menu, button". Another way you could use `aria-label` is on landmark elements:

```html
<nav aria-label="main navigation">...</nav>
```

Once a screen reader reaches the above HTML, it would announce "Main navigation, navigation landmark." If you had multiple navigation elements on a page, you could give each a different `aria-label` value in order to separate them from one another, making them more understandable for screen reader users. Pretty neat, huh?

**Do not** use `aria-label` to change how a word is phonetically announced. Certain words may not get announced correctly by a screen reader, and you may have a temptation to try and fix this. You may end up fixing how a word is announced by a screen reader, but that "fix" could end up making no sense when announced by other assistive technologies like a braille reader.

<br>

### `aria-labelledby`

The `aria-labelledby` attribute overrides both the native label and the `aria-label` attribute. When you use `aria-labelledby`, the accessible name of the target element is created by concatenating the text contents or `alt` attributes of the elements whose `id` are referenced.

The great thing about `aria-labelledby` is that not only can you pass in any number of `id` references, but you can also have an element reference itself. Keep in mind that you can't pass in the same reference multiple times, because any subsequent references after the first will be ignored.

```html
<!-- Here's the labeling element -->
<h2 id="label">Shirts</h2>

<!-- And here's the labeled element. Note the order of the ID references passed in -->
<button type="button" id="shop-btn" aria-labelledby="label shop-btn">
	Show Now
</button>
```

The HTML above would be announced by a screen reader as, "Shirts, shop now, button". This can make multiple "shop now" buttons on a page unique from one another and thus provide additional context, making the page more understandable.

Another great thing about `aria-labelledby` is that even if a labeling element is visually hidden, either by the `hidden` HTML attribute or with CSS, it will still modify the accessible name of the labeled element. This can be useful if you want to label an element for users of assistive technologies, but you don't want that element's label (or labels) to be visible to sighted users.

Although it may work somewhat similarly to the native `<label>` element, `aria-labelledby` does not have the same event handling by default. This is functionality you would have to add in yourself via JavaScript.

```html
<!-- Clicking the <label> element gives focus to the input element -->
<label for="name">Name:</label>
<input id="name" type="text" />

<!-- Clicking the <div> element won't give focus to the input element -->
<div id="label">Name:</div>
<input type="text" aria-labelledby="label" />
```

<br>

### `aria-describedby`

The `aria-describedby` attribute modifies the description property in the accessibility tree. Similar to the `aria-labelledby` attribute, when you use this attribute, you pass in the `id` values of other elements as the `aria-describedby` value, and the elements whose `id` values are passed in can also be visually hidden.

```html
<label
	>Password:
	<input type="password" aria-describedby="password-requirements" />
</label>

<!-- Meaningful text + ARIA! -->
<span id="password-requirements"
	>Password must be at least 10 characters 10.</span
>
```

When the `<input>` element receives focus, a screen reader would announce, "Password, edit protected, password must be at least ten characters long." This immediately notifies a screen reader user of any requirements for the password they want to choose any time the input receives focus.

<br>

## Hiding content from the accessibility tree

Similar to how you can visually hide elements with the `hidden` HTML attribute or the `display` and `visibility` CSS properties, you can use the `aria-hidden` attribute to hide certain elements, such as decorative images and icons, from the accessibility tree. The difference with `aria-hidden`, however, is that the element will remain visible to sighted users. This can be especially useful when you want to add an icon inside or another element. For example, if we were to use Material Icons inside of a button:

```html
<!-- Example 1 -->
<button type="button">
	<span class="material-icons">add</span>
	Add Book
</button>

<!-- Example 2 -->
<button type="button">
	<span class="material-icons" aria-hidden="true">add</span>
	Add Book
</button>
```

While both of the above examples would look visually identical, the button in Example 1 would be announced by a screen reader as, "Add add book, button". The text content of the `<span>` and the text content of the button itself are concatenated as the accessible name of the button. The button in Example 2, however, hides the `<span>` from the accessibility tree so its text content _isn't_ added to the button's accessible name, meaning a screen reader would correctly announce "Add book, button."

Be careful when using this attribute, though. When you give an element `aria-hidden="true"`, all children of that element will also become hidden to the accessibility tree. Adding `aria-hidden="false"` to a child element won't have any effect if one of its parents still has `aria-hidden="true"`, either.

You should also be careful not to give an element `aria-hidden="true"` if it is focusable. Doing so would cause nothing to be announced when the element receives focus, which would confuse users that use a screen reader and navigate the page via a keyboard.

<br>

## Knowledge check

- ##### What purpose does WAI-ARIA serve?

The purpose of WAI-ARIA is to define a way to make web content more accessible when native HTML is unable to do so.

<br>

- ##### What are the four things ARIA can't do?

The four things ARIA can't do are:

- modify an element's appearance,

- modify an element's behavior,

- add focusability, or

- add keyboard event handling.

<br>

- ##### What the five rules of ARIA?

The five rules of ARIA are as follows:

1. Always use native HTML elements and attributes over ARIA when possible.

2. Never change native semantics, unless you have no other choice.

3. All interactive ARIA controls must be usable with a keyboard.

4. Never use `role="presentation" or `aria-hidden="true"` on focusable elements.

5. All interactive elements must have an accessible name.

<br>

- ##### What is the accessibility tree?

While the DOM represents nodes and objects that make up a web page, the accessibility tree contains only the accessibility related information that will be used by assistive technologies.

<br>

- ##### What does the `aria-hidden` attribute do?

The `aria-hidden` attribute hides the element from assistive technology users, along with its children.
