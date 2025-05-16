# [Media Queries](https://www.theodinproject.com/lessons/node-path-advanced-html-and-css-media-queries)

## Introduction

With media queries, it is possible to completely restyle your web projects based on the size of a user's screen. All of the lessons we've had so far have focused on making sure that the individual elements of your layout are as flexible as possible, but sometimes you will need to actually _change_ some of your CSS values to accomodate a specific screen size. These changes could be subtle shifts, such as adjusting margin, padding, or font-size to squeeze more content onto the screen, or they could be big obvious shifts in layout. The nature of the exact changes will depend on your design, but the underlying technique is the same.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- You'll learn how to implement media queries to create fully responsive websites that look great on any device.

<br>

## Media query syntax

The basic syntax for media queries is as follows:

```css
body {
	margin: 24px;
}

@media (max-width: 600px) {
	body {
		margin: 8px;
	}
}
```

In the above example, the margin is changed based on screen size. Specifically, on all screens _below or equal_ to 600px, the margin will be `8px`, and on all screens _above_ `600px`, it will be `24px`.

Really, that's all there is to it. You can create some complex shifting layouts with just this knowledge alone. You can create an unlimited number of media queries in a single document.

[Demo on CodePen](https://codepen.io/TheOdinProjectExamples/pen/yLzYgZw)

You can also put any number of style definitions inside a media query:

[Demo on CodePen](https://codepen.io/TheOdinProjectExamples/pen/XWempGr)

<br>

### Tips

#### Other queries

In all of the above examples, our queries specify a `max-width` which will apply styles to any screen resolution _below_ or equal to the specified value. Said another way: a `max-width` query will apply on any screen up to the defined `max-width`. It is also possible to define a `min-width`, which applies to any screen resolution _above_ or equal to the given value. `max-height` and `min-height` are also valid.

#### Limit media queries

As mentioned earlier, it is possible to create an unlimited number of media queries for every possible screen size. However, it is best to minimize your media-query usage and rely more on the natural flexibility of your layouts. Consider the second embedded example above ("my cool site"). It only _needs_ one media query to accomodate all desktop and mobile sizes, and there's no real need to create more.

#### Common breakpoints

'Breakpoint' is the term for the screen size that triggers your media query. You will find quite a lot of differing opinions on what exactly your breakpoints should be. In general, it's helpful to think about the kinds of devices and screens that your users will be using. Mobile phones are usually under `500px`. Tablets are often between `500px` and `1000px`. Anything larger than `1000px` is likely to be a normal browser screen. Super wide screens are also becoming more common, which means that your site _could_ end up being viewed on a screen wider than `2000px`!

This does _not_ mean that you should just start your project with media queries for each device. Each project is going to have different requirements based on the design you're trying to achieve. As mentioned above, try to limit your breakpoints to just what you _need_. With many relatively basic layouts, you can get by with only one mobile-centric breakpoint somewhere around `500`-`600px`. More complex layouts might benefits from doing a full-sized layout above `1200px`, an altered "tablet" layout between `600px` and `1200px` and mobile below `600px`. The real takeaway here is that it doens't really matter exactly where you set your breakpoints, just do what makes sense for your project.

#### Zooming!

In most browsers, **zooming in on a webpage will change the effective resolution of that page**. If your browser window is exactly `1000px` wide, zooming in will cause the page to behave as if the screen is _smaller_, and will trigger media queries based on the simulated/zoomed screen resolution. Zooming _out_ can be handy for debugging issues that arise on screens that are larger than your own computer screen. Forgetting that you've zoomed in or out on a webpage can cause some real confusion when breakpoints refuse to trigger at the correct points.

<br>

## Print styles

You'll often see media queries defined with the `screen` keyword like so:

```css
@media screen and (max-width: 480px) {
}
```

This is not necessary, but it _does_ point toward another very useful capability of media queries: changing styles based on the media type. Everything we've covered so far has been specifically intended for viewing on some kind of screen so specifying `screen` is redundant. However, it is possible to create a different set of styles for your website when it is sent to your printer or viewed in print-preview mode by using the `print` keyword.

```css
@media print {
	/* print styles go here */
}
```

This is not something we're going to focus on in our curriculum, but it may be something you want to consider taking advantage of in some cases. It's fairly common to change some colors (i.e. make things black/white), and add `display: none` to hide elements that are useless in a printed environment (buttons, nav links, etc).

<br>

## Knowledge check

- ##### How do you define a media query to create a mobile layout for your site?

You use `@media screen and (max-width: 480px) {}` or something similar.

<br>

- ##### What is the difference between `max-width` and `min-width` in a media query definition?

The `max-width` in media query definition means that the following style will apply to screens with a max-width of `px`, meaning any screen size lower than the specified number. While `min-width` in a media query definition means that the following styles will apply to screens with that minimum with, meaning any screen size higher than the specified number.

<hr>
<br>
<br>

# [Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)

**Media queries** allow you to apply CSS styles depending on a device's media type (such as print vs. screen) or other features or characteristics such as screen resolution or orientation, aspect ratio, browser viewport width or height, user preferences such as preferring reduced motion, data usage, or transparency.

Media queries are used for the following:

- To conditionally apply styles with the CSS `@media` and `@import` at-rules.

- To target specific media for the `<style>`, `<link>`, `<source>`, and other HTML elements with the `media=` or `sizes=` attributes.

- To test and monitor media states using the `Window.matchMedia()` and `EventTarget.addEventListener()` methods.

> **Note:** The examples on this page use CSS's `@media` for illustrative purposes, but the basic syntax remains the same for all types of media queries.

<br>

## Syntax

A media query is composed of an optional _media_ type and any number of _media feature_ expressions, which may optionally be combined in various ways using _logical operators_. Media queries are case-insensitive.

- Media types define the broad category of device for which the media query applies: `all`, `print`, `screen`. The type is optional (assumed to be `all`) except when using the `only` logical operator.

- Media features describe a specific characteristic of the user agent, output device, or environment:

  - `any-hover`

  - `any-pointer`

  - `aspect-ratio`

  - `color`

  - `color-gamut`

  - `color-index`

  - `device-aspect-ratio` (deprecated)

  - `device-height` (deprecated)

  - `device-posture`

  - `device-width` (deprecated)

  - `display-mode`

  - `forced-colors`

  - `grid`

  - `height`

  - `hover`

  - `inverted-colors`

  - `monochrome`

  - `orientation`

  - `overflow-block`

  - `overflow-inline`

  - `pointer`

  - `prefers-color-scheme`

  - `prefers-contrast`

  - `prefers-reduced-motion`

  - `prefers-reduced-transparency`

  - `resolution`

  - `scripting`

  - `update`

  - `video-dynamic-range`

  - `width`

  For example, the `hover` feature allows a query to check whether the device supports hovering over elements. Media feature expressions test for their presence or value, and are entirely optional. Each media feature expression must be surrounded by parenteses.

- Logical operators can be used to compose a complex media query: `not`, `and`, and `only`. You can also combine multiple media queries into a single rule by separating them with commas.

A media query computes to `true` when the media type (if specified) matches the device on which a document is being displayed _and_ all media feature expressions compute as true. Queries involving unknown media types are always false.

> **Note:** A style sheet with a media query attached to its `<link>` tag will still download even if the query returns `false`, the download will happen but the priority of downloading will be much lower. Nevertheless, its content will not apply unless and until the result of the query changes to `true`. You can read why this happens in Tomayac's blog [Why Browser Download Stylesheet with Non-Matching Media Queries](https://medium.com/@tomayac/why-browsers-download-stylesheets-with-non-matching-media-queries-eb61b91b85a2).

<br>

## Targeting media types

Media types describe the general category of a given device. Although websites are commonly designed with screens in mind, you may want to create styles that target special devices such as printers or audio-based screen readers. For example, this CSS targets printers:

```css
@media print {
	/* ... */
}
```

You can also target multiple devices. For instance, this `@media` rule uses two media queries to target both screen and print devices:

```css
@media screen, print {
	/* ... */
}
```

See [media types](https://developer.mozilla.org/en-US/docs/Web/CSS/@media#media_types) for the list of available media types. Because media types describe devices in very broad terms, most of the originally-defined media types were deprecated, with just `screen`, `print`, and `all` remaining. To target more specific attributes, use _media features_ instead.

<br>

## Targeting media features

Media features describe the specific characteristics of a given [user agent](https://developer.mozilla.org/en-US/docs/Glossary/User_agent), output device, or environment. For instance, you can apply specific styles to widescreen monitors, computers that use mice, devices that are being used in low-light conditions. This example applies styles when the user's _primary_ input mechanism (such as a mouse) can hover over elements:

```css
@media (hover: hover) {
	/* ... */
}
```

Media features are either range or discrete.

<br>

_Discrete features_ take their value from an [enumerated](https://developer.mozilla.org/en-US/docs/Glossary/Enumerated) set of possible keyword values. For example, the discrete `orientation` feature accepts either `landscape` or `portrait`.

```css
@media print and (orientation: portrait) {
	/* ... */
}
```

Many _range features_ can be prefixed with "min-" or "max-" to express "minimum condition" or "maximum condition" constraints. For example, this CSS will apply styles only if your browser's viewport width is equal to or narrower than 1250px:

```css
@media (max-width: 1250px) {
	/* ... */
}
```

The following media queries are equivalent to the above example:

```css
@media (width <= 1250px) {
	/* ... */
}

@media (1250px >= width) {
	/* ... */
}
```

With media query range features, you can either use the inclusive `min-` and `max-` prefixes or the more concise range syntax operators `<=` and `>=`.

The following media queries are equivalent:

```css
@media (min-width: 30em) and (max-width: 50em) {
	/* ... */
}

@media (50em >= width >= 30em) {
	/* ... */
}

@media (30em <= width <= 50em) {
	/* ... */
}
```

The range comparisons above are inclusive. To exclude the comparison value, use `<` and/or `>`.

```css
@media (30em < width < 50em) {
	/* ... */
}

@media (50em > width > 30em) {
	/* ... */
}
```

If you create a media feature query without specifying a value, the nested styles will be used as long as the feature's value is not `0` or `none`. For example, this CSS will apply to any device with a color screen:

```css
@media (color) {
	/* ... */
}
```

If a feature doesn't apply to the device on which the browser is running, expressions involving that media feature are always false.

For more [Media feature](https://developer.mozilla.org/en-US/docs/Web/CSS/@media#media_features) examples, please see the reference page for each specific feature.

<br>

## Creating complex media queries

Sometimes you may want to create a media query that depends on multiple conditions. This is where the _logical operators_ come in: `not`, `and`, and `only`. Furthermore, you can combine multiple media queries into a comma-separated list; this allows you to apply the same styles in different situations, with the contained media queries evaluated as a logical `or` composition: interpreted as if each media query were within parentheses with an `or` between them.

In the previous example, we saw the `and` operator used to group a media _type_ with a media _feature_. The `and` operator can also combine multiple media features within a single media query. The `not` operator negates a media query, or a media feature when used with brackets, basically reversing their normal meanings. The `or` operator can, under certain conditions, be used to combine multiple media features within a single media query. Lastly, the `only` operator was used to prevent older browsers from applying the styles without evaluating the media feature expressions but it has no effect in modern browsers.

> **Note:** In most cases, the `all` media type is used by default when no other type is specified. However, if you use the `only` operator, you must explicitly specify a media type. You can see `only screen` or `only print` as a whole.

<br>

### Combining multiple types or features

The `and` keyword combines a media feature with a media type _or_ other media features. This example combines two media features to restrict styles to landscape-oriented devices with a width of at least 30ems.

```css
@media (min-width: 30em) and (orientation: landscape) {
	/* ... */
}
```

To limit the styles to devices with a screen, you can chain the media features to the `screen` media type:

```css
@media screen and (min-width: 30em) and (orientation: landscape) {
	/* ... */
}
```

<br>

### Testing for multiple queries

You can use a comma-separated list of media queries to apply styles when the user's device matches any one of various media types, features, or states.

The following rule contains two media queries. The block's styles will apply if either the user's device has a height of 680px or more _or_ if the browser viewport is in portrait mode (the viewport height is greater than the viewport width):

```css
@media (min-height: 680px), screen and (orientation: portrait) {
	/* ... */
}
```

In this example, if the user is printing to a PDF and the page height is 800px, the media query returns true because the first query component -- which tests whether the viewport has a height of `680px` or more -- is true. Likewise, if a user is on a smartphone in portrait mode with a viewport height of 480px, the media query returns true because the second query component is true.

In a comma-separated list of media queries, the individual media queries at the comma or, in the case of the last media query in the list, at the opening bracket (`{`).

<br>

### Inverting a query's meaning

The `not` keyword inverts the meaning of a single media query. For example, the CSS styles in this media query will apply to everything _except_ printed media:

```css
@media not print {
	/* ... */
}
```

The `not` negates only the media query it is applied to. The `not`, without parenthesis, negates all the features within the media query in which it is contained. This means, in a comma-separated list of media queries, each `not` applies to the single query it is contained within, applying to _all_ the features within that single query. In this example, the `not` applies to the first media query, which concludes at the first comma:

```css
@media not screen and (color), print and (color) {
	/* ... */
}
```

The above query is evaluated like this:

```css
@media (not (screen and (color))), print and (color) {
	/* ... */
}
```

Both examples are valid. Media conditions can be grouped by wrapping them in parentheses (`()`). These groups can then be nested within a condition the same as a single media query.

The `not` is evaluated last in a media query, meaning it applies to the entire media query, not to a single feature within a feature, as if an open parenthesis was added immediately after the `not` and closed at the end of the media query.

The following query:

```css
@media not all and (monochrome) {
	/* ... */
}
```

is evaluated like this:

```css
@media not (all and (monochrome)) {
	/* ... */
}
```

It is not evaluated like this:

```css
@media (not all) and (monochrome) {
	/* ... */
}
```

To negate a single feature within a media query, use parenthesis. Encompassing a `not` and a media feature in parentheses limits the components of the query that get negated.

In this example, we negate the `hover` media feature but not the `all` media type:

```css
@media all and (not(hover)) {
	/* ... */
}
```

The `not(hover)` matches if the device has no hover capability. In this case, because of the parentheses, the `not` applies to `hover` but not to `all`.

<br>

### Improving compatibility with older browsers

The `only` keyword prevents older browsers that do not support media queries with media features from applying to given styles. _It has no effect on modern browsers._

```css
@media only screen and (color) {
	/* ... */
}
```

<br>

### Testing for multiple features with `or`

You can use `or` to test for a match among more than one feature, resolving to `true` if any of the features are true. For example, the following query tests for devices that have a monochrome display or hover capability:

```css
@media (not (color)) or (hover) {
	/* ... */
}
```

Note that you cannot use the `or` operator on the same level as the `and` and `not` operators. You can either separate the media features with a comma or use parenthesis to group sub-expressions of media features to clarify the order of evaluation.

For example, the following queries are both valid:

```css
@media ((color) and (hover)) or (monochrome) {
	/* ... */
}

/* or */
@media (color) and (hover), (monochrome) {
	/* ... */
}
```
