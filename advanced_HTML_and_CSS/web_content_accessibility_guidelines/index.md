# [The Web Content Accessibility Guidelines (WCAG)](https://www.theodinproject.com/lessons/node-path-advanced-html-and-css-the-web-content-accessibility-guidelines-wcag)

## Introduction

After the previous lesson, you should now have a better understanding of how important web accessibility can be for certain users, and how beneficial it can be for _all_ users. But how do we know not only what should be a11y friendly, but how to make those things a11y friendly? Well, there are many sources available to tell us what and how, those who actually rely on accessibility being one of the best sources we can consult.

Another source, one that goes over many different ways to make websites more accessible, is the Web Content Accessibility Guidelines (WCAG). In this lesson, we're going to skim the surface of the WCAG, just to familiarize you with them at a more basic level.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Explain the purpose of the Web Content Accessibility Guidelines

- Name the 4 principles of the WCAG.

<br>

## Web Content Accessibility Guidelines

The WCAG exist in order to help create a shared standard when it comes to web accessibility. Think of web accessibility as the destination, and the WCAG as one of the tools that can help get us closer to it.

It's important to understand that while the WCAG can be incredibly helpful for building an a11y foundation, they are not he finish line when it comes to accessibility. Like the name says, they are guidelines, and they will only help us make website _more_ accessible.

<br>

## The four principles

The WCAG Are organized around four, core principles (POUR) that should be kept in mind when implementing any sort of accessibility feature:

1. **Perceivable:** Users must be able to perceive the information or user interfaces being presented. For example, light text on a light background could be difficult for some users with a visual impairment to perceive.

2. **Operable:** Users must be able to operate any user interfaces or navigation, and interfaces cannot require an interaction which the user cannot perform. A navigation bar with drop-down menus that only expand when a mouse cursor hovers over them, for example, would not be operable by keyboard users giving those menu items focus.

3. **Understandable:** Users must be able to undestand any information or user interface that is presented to them. For example, if a user tried submitting a form and received an error such as "Error 113: Bad data", they wouldn't be able to understand what the error actually means or how to fix whatever caused the error.

4. **Robust:** Content must be accessible by current assistive technologies and other user agents, and must remain accessible as those technologies advance.

### Conformance levels

Conformance levels get mentioned at a couple of other points in these lessons, and we're only mentioning them here to briefly explain what they are ahead of time. The WCAG has three different conformance levels, each of which is made up of various success criteria, or rules, that must be followed in order to successfully meet that level of conformance. You don't need to worry about meeting any of these conformance levels completely for the purposes of these lessons, you only need to know that they exist (luckily their naming is pretty easy to remember).

- **Level A**, or essential support, is the minimum level of conformance for the WCAG.

- **Level AA**, or ideal support, is the level many organizations strive for. Metting this level also requires meeting Level A.

- **Level AAA**, or specialized support, isn't recommended for entire sites to meet in full, as some content may make it impossible to meet this conformance level. Meeting this level would require also meeting both Level A and Level AA.

<br>

## (Before) implementing accessibility

The lessons that follow dive into several concepts that can help you improve the accessibility of your websites, but they don't cover _every_ facet of accessibility. The goal of these lessons is just to introduce you to some of the more common concepts that you should get into the habit of checking for moving forward.

Even though we're only introducing you to some of these a11y concepts, you may still worry that your site isn't accessible enough. The first thing to keep in mind is that **no site will ever be 100% accessible**, so don't try to aim for such an impossible goal. Sometimes the purpose or concept of a site even requires some things to not be accessible in certain ways.

The second thing to keep in mind is that just taking those first few steps towards creating accessible websites matters just as much as the many more steps you'll take in the future. Even if you only add one a11y feature to your websites for now, what you may think is a minor addition could actually be a huge improvement for more users than you realize. So don't feel like you have to make everything perfect or that you need to add everything at once when implementing accessibility, especially when you're just starting out.

<br>

## Knowledge check

- ##### What is the purpose of the Web Content Accessibility Guidelines?

The WCAG exists in order to help create a shared standard when it comes to web accessibility.

<br>

- ##### What are the 4 principles of the WCAG?

The 4 principles of the WCAG is POUR in abbreviation which means Perceivable, Operable, Understandable, and Robust.

<hr>
<br>
<br>

# [WCAG 2 Overview](https://www.w3.org/WAI/standards-guidelines/wcag/)

## Introduction

Web Content Accessibility Guideline (WCAG) 2 is developed through the W3C process in cooperation with individuals and organizations around the world, with a goal of providing a single shared standard for web content accessibility that meets the needs of individuals, organizations, and governments internationally.

The WCAG documents explain how to make web content more accessible to people with disabilities. Web "content" generally refers to the information in a web page or web application, including:

- natural information such as text, images, and sounds

- code or markup that defines structure, presentation, etc.

<br>

## Who WCAG is for

WCAG is for those who want a technical standard. **It is not an introduction to accessibility.**

WCAG is primarily intended for:

- Web content developers (page authors, site designers, etc.)

- Web authoring tool developers

- Web accessibility evaluation tool developers

- Others who want or need a standard for web accessibility, including mobile accessibility

To meet the needs of others -- including policy makes, managers, and researchers -- there are many different WAI Resources.

<br>

## What is in WCAG 2

The WCAG 2.2 has 13 guidelines. The guidelines are organized under 4 principles: perceivable, operable, understandable, and robust.

For each guideline, there are testable _success critera_. The success criteria are at three levels: A, AA, and AAA.

The success criteria are what determine "conformance" to WCAG. That is, in order to meet WCAG, the content needs to meet the success criteria.

<br>

### Supporting material and supplemental guidance

The following resources help you understand and implement WCAG, and improve accessibility beyond WCAG:

- Quick Reference / How to Meet WCAG 2 / Checklist

- Understanding WCAG 2

- Techniques for WCAG 2

- Test Rules for WCAG 2

- Supplemental Guidance

<br>

## WCAG 2.0, 2.1, 2.2

The Web Content Accessibility Guidelines (WCAG) standards are referenceable when they are published as a 'W3C Recommendation' web standard.

- WCAG 2.0 was published on 11 December 2008.

- WCAG 2.1 was published on 5 June 2018, and updates were published on 21 September 2023 and 12 December 2024.

- WCAG 2.2 was published on 5 October 2023, and an update was published on 12 December 2024.

WCAG 2.0, 2.1, and 2.2 are designed to be "backwards compatible", which meant content that conforms to WCAG 2.2 also conforms to WCAG 2.1 and WCAG 2.0. If you want to meet all the versions, you can use the WCAG 2.2 resources and you don't need to bother looking at earlier versions.

All the success criteria from 2.0 are included in 2.1, and all from 2.1 are in 2.2.

- WCAG 2.0 has 12 guidelines.

- WCAG 2.1 adds 1 guideline and 17 success criteria.

- WCAG 2.2 adds 9 success criteria.

A few things have changed and we intend the updates in the related documents to support backwards compatibility in practice. The main change is that in WCAG 2.2, once success criteria (4.1.1 Parsing) is obsolete. Notes added to WCAG 2.1 and WCAG 2.0 errata address this. WCAG 2.2 also includes Notes about different languages.

WCAG 2.0, WCAG 2.1, and WCAG 2.2 are all existing standards. WCAG 2.2 does not deprecate or supersede WCAG 2.1, and WCAG 2.1 does not deprecate or supersede WCAG 2.0. W3C encourages you to use the most recent version of WCAG.

<br>

## WCAG 2.0 is ISO/IEC 40500

WCAG 2.0 is approved as an ISO standard: ISO/IEC 40500:2012. ISO/IEC 40500 is exactly the same as the original WCAG 2.0, which is introduced above along with supporting resources.

**W3C submitted WCAG 2.2 to ISO.** It will likely be after June 2025 before the ISO process is complete.

<br>

## Who develops WCAG

The WCAG technical documents are developed by the Accessibility Guidelines Working Group (AG WG) (_formerly the Web Content Accessibility Guidelines Working Group_), which is part of the World Wide Web Consortium (W3C) Web Accessibility Initiative (WAI).

WAI updates Techniques for WCAG 2 and Understanding WCAG 2 periodically.

<br>

## WCAG 3 and more infomation

WCAG is part of a series of accessibility guidelines, including the Authoring Tool Accessibility Guidelines (ATAG) and the User Agent Accessibility Guidelines (UAAG).

<hr>
<br>
<br>

# [WebAIM's WCAG 2 Checklist](https://webaim.org/standards/wcag/checklist)

> The following is **NOT** the Web Content Accessibility Guidelines (WCAG) 2. It is a checklist that presents our recommendations for implementing the most common accessibility principles and techniques for those seeking WCAG conformance. The language used here significantly simplifies and condenses the official WCAG 2.2 specification and supporting materials to make it easier to implement and verify for web pages. The checklist contains links to the official success criteria.

<br>

## Perceivable

Web content is made available to the senses - sight, hearing, and/or touch.

> #### Guideline 1.1
>
> Provide text alternatives for any non-text content

#### 1.1.1 Non-text Content (A, 2.0)

- Images, image buttons, and image map hot spots have apppropriate, equivalent alternative text.

- Images that do not convey content, are decorative, or contain content that is already conveyed in text are given empty alternative text (`alt=""`) or implemented as CSS backgrounds. All linked images have descriptive alternative text.

- Equivalent alternatives to complex images are provided in content or on a separate linked page.

- Form buttons have a descriptive value.

- Inputs have associated accessible names.

- Embedded multimedia is identified via accessible text.

- Frames and iframes are appropriately titled.

> #### Guideline 1.2
>
> Provide alternatives for time-based media.

NOTE: If the audio or video is designated as an alternative to web content (e.g., an audio or sign language version of a web page), then the web content itself serves as the alternative.

#### 1.2.1 Audio-only and Video-only (Prerecorded) (A, 2.0)

- A descriptive transcript of relevant content is provided for non-live audio-only (audio podcasts, MP3 files, etc.).

- A descriptive transcript or audio description of the relevant content is provided for non-live video-only, unless the video is decorative.

#### 1.2.2 Captions (Prerecorded) (A, 2.0)

- Synchronized captions are provided for non-live video (YouTube videos, etc.).

#### 1.2.3 Audio Description or Media Alternative (Prerecorded) (A, 2.0)

- A descriptive transcript **or** audio description is provided for non-live video.

NOTE: Only required if there is relevant visual content that is not presented in the audio.

#### 1.2.4 Captions (Live) (AA, 2.0)

- Synchronized captions are provided for live media that contains audio (audio-only broadcasts, web casts, video conferences, etc.).

#### 1.2.5 Audio Description (Preprecorded) (AA, 2.0)

- Audio descriptions are provided for non-live video.

NOTE: Only required if there is relevant visual content that is not presented in the audio.

- While not required at Level AA, for optimal accessibility WebAIM recommends descriptive transcripts in addition to audio descriptions.

> #### Guideline 1.3
>
> Create content that can be presented in different ways (for example simpler layout) without losing information or structure.

#### 1.3.1 Info and Relationships (A, 2.0)

- Semantic markup is appropriately used to designate headings, regions/landmarks, lists, emphasized or special text, etc.

- Tables are used for tabular data and data cells are associated with their headers. Data table captions, if present, are associated to data tables.

- Text labels are associated with form inputs. Related form controls are grouped with fieldset/legend. ARIA labelling may be used when standard HTML is insufficient.

#### 1.3.2 Meaningful Sequence (A, 2.0)

- The reading and navigation order (determined by code order) is logical and intuitive.

#### 1.3.3 Sensory Characteristics (A, 2.0)

- Instructions do not rely upon shape, size, or visual location (e.g., "Click the square icon to continue" "Instructions are in the right-hand column).

- Instructions do not rely upon sound (e.g., "A beeping sound indicates you may continue".).

#### 1.3.4 Orientation (AA, 2.1)

- Orientation of web content is not restricted to only portrait or landscape, unless a specific orientation is necessary.

#### 1.3.5 Identify Input Purpose (AA, 2.1)

- Input fields that collect certain types of user information have an appropriate `autocomplete` attribute defined.

> #### Guideline 1.4
>
> Make it easier for users to see and hear content including separating foreground from background.

#### 1.4.1 Use of Color (A, 2.0)

- Color is not used as the sole method of conveying content or distinguishing visual elements.

- Color alone is not used to distinguish links from surrounding text unless the contrast ratio between the link and the surrounding text is at least 3:1 _and_ an additional distinction (e.g., it becomes underlined) is provided when the link is hovered over and receives keyboard focus.

#### 1.4.2 Audio Control (A, 2.0)

- A mechanism is provided to stop, pause, mute, or adjust volume for audio that auomatically plays on a page for more than 3 seconds.

#### 1.4.3 Contrast (Minimum) (AA, 2.0)

- Text and images of text have a contrast ratio of at least 4.5:1.

- Large text - at least 18 point (typically 24px) or 14 point (typically 18.66px) and bold - has a contrast ratio of at least 3:1.

#### 1.4.4 Resize text (AA, 2.0)

- The page is readable and functional when the page is zoomed to 200%.

NOTE: 1.4.10 (below) introduces additional requirements for zoomed content.

#### 1.4.5 Images of Text (AA, 2.0)

- If the same visual presentation can be made using text alone, an image is not used to present that text.

#### 1.4.10 Reflow (AA, 2.1)

- No loss of content or functionality orrurs, and horizontal scrolling is avoided when content is presented at a width of 320 pixels.

  - This requires responsive design for most web sites. This is best tested by setting the browser window to 1280 pixels wide and then zooming the page content to 400%.

- Content that requires horizontal scrolling, such as data tables, complex images (such as maps and charts), toolbars, etc. are exempted.

#### 1.4.11 Non-text contrast (AA, 2.1)

- A contrast ratio of at least 3:1 is present for differentiating graphical objects (such as icons and components of charts or graphs) and author-customized interface components (such as buttons, form controls, and focus indicators/outlines).

- At least 3:1 contrast is maintained in the various states (focus, hover, active, etc.) of author-customized interactive components.

#### 1.4.12 Text Spacing (AA, 2.1)

- No loss of content or functionality occurs when the user adapts paragraph spacing to 2 times the font size, text line height/spacing to 1.5 times the font size, word spacing to .16 times the font size, and letter spacing to .12 times the font size.

- This is best supported by avoiding pixel height definitions for elements that contain text.

#### 1.4.13 Content on Hover or Focus (AA, 2.1)

- When additional content is presented on hover or keyboard focus:

  - The newly revealed content can be dismissed (generally via the Esc key) without moving the pointer or keyboard focus, unless the content presents an input error or does not obscure or interfere with other page content.

  - The pointer can be moved to the new content without the content disappearing.

  - The new content must remain visible until the pointer or keyboard focus is moved away from the triggering control, the new content is dismissed, or the new content is no longer relevant.

<br>

## Operable

Interface forms, controls, and navigation are operable.

> #### Guideline 2.1
>
> Make all functionality available from a keyboard.

#### 2.1.1 Keyboard (A, 2.0)

- All page functionality is available using the keyboard, unless the functionality cannot be accomplished in any known way using a keyboard (e.g., free hand drawing).

- Page-specified shortcut keys and accesskeys (accesskey should typically be avoided) do not conflict with existing browser and screen reader shortcuts.

#### 2.1.2 No Keyboard Trap (A, 2.0)

- Keyboard focus is never locked or trapped at one particular page element. The user can navigate to and from all navigable page elements using only a keyboard.

#### 2.1.4 Character Key Shortcuts (A, 2.1)

- If a keyboard shortcut uses printable character keys, then the user must be able to disable the key command, change the defined key to a non-printable key (Ctrl, Alt, etc.), or only activate the shortcut when an associated interface component or button is focused.

> #### Guideline 2.2
>
> Provide users enough time to read and use content.

#### 2.2.1 Timing Adjustable (A, 2.0)

- If a page or application has a time limit, the user is given options to turn off, adjust, or extend that time limit. This is not a requirement for real-time events (e.g., an auction), where the time limit is absolutely required, or if the time limit is longer than 20 hours.

#### 2.2.2 Pause, Stop, Hide (A, 2.0)

- Automatically moving, blinking, or scrolling content (such as carousels, marquees, or animations) that lasts longer than 5 seconds can be paused, stopped, or hidden by the user.

- Automatically updating content (e.g., a dynamically-updating news ticker, chat messages, etc.) can be paused, stopped, or hidden by the user or the user can manually control the timing of the updates.

> #### Guideline 2.3
>
> Do not design content in a way that is known to cause seizures.

#### 2.3.1 Three Flashes or Below Threshold (A, 2.0)

- No page content flashes more than 3 times per second unless that flashing content is sufficiently small and the flashes are of low contrast and do not contain too much red.

> #### Guideline 2.4
>
> Provide ways to help users navigate, find content, and determine where they are.

#### 2.4.1 Bypass Blocks (A, 2.0)

- A link is provided to skip navigation and other page elements that are repeated across web pages.

- While proper use of headings or regions/landmarks is sufficient to meet this success criterion, because keyboard navigation by headings or regions is not supported in most browsers, WebAIM recommends a "skip" link in addition to headings and regions.

#### 2.4.2 Page Titled (A, 2.0)

- The web page has a descriptive and informative page title.

#### 2.4.3 Focus Order (A, 2.0)

- The navigation order of links, form controls, etc. is logical and intuitive.

#### 2.4.4 Link Purpose (In Context) (A, 2.0)

- The purpose of each link (or image button or image map hotspot) can be determined from the link text alone, or from the link text and its context (e.g., surrounding text, list item, previous heading, or table headers).

- Links with the same text that go to different locations are readily distinguishable.

#### 2.4.5 Multiple Ways (AA, 2.0)

- Multiple ways are available to find other web pages on the site - at least two of: a list of related pages, table of contents, site map, site search, or list of all available web pages.

#### 2.4.6 Headings and Labels (AA, 2.0)

- Page headings and labels for form and interactive controls are informative. Avoid duplicating heading and label text unless the structure provides adequate differentiation between them.

#### 2.4.7 Focus Visible (AA, 2.0)

- There is a visible indicator for page elements when they receive keyboard focus.

#### 2.4.11 Focus Not Obscured (Minimum) (AA, 2.2)

- When elements have keyboard focus, they are not entirely covered or hidden by page content.

> #### Guideline 2.5
>
> Make it easier for users to operate functionality through various inputs beyond keyboard.

#### 2.5.1 Pointer Gestures (A, 2.1)

- If multipoint or path-based gestures (such as pinching, swiping, or dragging across the screen) are not essential to the functionality, then the functionality can also be performed with a single point activation (such as activating a button).

#### 2.5.2 Pointer Cancellation (A, 2.1)

- To help avoid inadvertent activation of controls, avoid non-essential down-event (e.g., `onmousedown`) activation when clicking, tapping, or long pressing the screen. For complex interactions (such as drag and drop), `onmousedown` can be used if an associated `onmouseup` (or similar) event can be aborted or reversed.

#### 2.5.3 Label in Name (A, 2.1)

- If an interface component (link, button, etc) presents text (or images of text), the accessible name (label, alternative text, aria-label, etc.) for that component must include the visible text.

#### 2.5.4 Motion Actuation (A, 2.1)

- Functionality that is triggered by moving the device (such as shaking or panning a mobile device) or by user movement (such as waving to camera) can be disabled and equivalent functionality is provided via standard controls like buttons.

#### 2.5.7 Dragging Movements (AA, 2.2)

- Functionality that uses pointer dragging can also be achieved using a single pointer without dragging (unless dragging is essential).

#### 2.5.8 Target Size (Minimum) (AA, 2.2)

- Pointer input target sizes are at least 24 by 24 pixels unless:

  - A 24 pixel diameter circle centered on the target element does not intersect with any other target or a 24 pixel circle centered on an adjacent target.

  - The functionality can be achieved in some other conformant manner.

  - The target is in a sentence or list.

  - The target size can't be modified or is essential to the functionality.

<br>

## Understandable

Information and the operation of user interface must be understandable.

> #### Guideline 3.1
>
> Make text content readable and understandable.

#### 3.1.1 Language of Page (A, 2.0)

- The language of the page is identified using the `lang` attribute (e.g., `<html lang="en">).

#### 3.1.2 Language of Parts (AA, 2.0)

- The language of page content that is in a different language is identified using the `lang` attribute (e.g., `<blockquote lang="es">`)

> #### Guideline 3.2
>
> Make Web pages appear and operate in predictable ways.

#### 3.2.1 On Focus (A, 2.0)

- When a page element receives focus, it does not result in a substantial change to the page, the spawning of a pop-up window, an additional change of keyboard focus, or any other change that could confuse or disorient the user.

#### 3.2.2 On Input (A, 2.0)

- When a user inputs information or interacts with a control, it does not result in a substantial change to the page, the spawning of a pop-up window, an additional change of keyboard focus, or any other change that could confuse or disorient the user unless the user is informed of the change ahead of time.

#### 3.2.3 Consistent Navigation (AA, 2.0)

- Navigation links that are repeated on web pages do not change order when navigating through the site.

#### 3.2.4 Consistent Identification (AA, 2.0)

- Elements that have the same functionality across multiple web pages are consistently identified. For example, a search box at the top of the site should always be labeled the same way.

#### 3.2.6 Consistent Help (A, 2.2)

- Contact and self-help details or functionality are presented consistently when present on multiple web pages.

> #### Guideline 3.3
>
> Help users avoid and correct mistakes

#### 3.3.1 Error Identification (A, 2.0)

- Required inputs or inputs that require a specific format, value, or length provide this information within the element's label.

- Form validation errors are efficient, intuitive, and accessible. The error is clearly identified, quick access to the problematic element is provided, and the user can easily fix the error and resubmit the form.

#### 3.3.2 Labels or Instructions (A, 2.0)

- Inputs are identified by labels or instructions that help users know what information to enter.

#### 3.3.3 Error Suggestion (AA, 2.0)

- If an input error is detected (via client-side or server-side validation), suggestions are provided for fixing the input in a timely and accessible manner.

#### 3.3.4 Error Prevention (Legal, Financial, Data) (AA, 2.0)

- Submissions, changes, and deletions of legal, financial, or test data can be reversed, verified, or confirmed.

#### 3.3.7 Redundant Entry (A, 2.2)

- Information that a user must re-enter to complete a single-session process must be auto-populated or available for the user to select, unless re-entering the information is essential to the functionality, the information poses security issues, or the previously-entered information is no longer valid.

#### 3.3.8 Accessible Authentication (Minimum) (AA, 2.2)

- A cognitive function test (such as remembering a password or solving a puzzle) is not required for any step in an authentication process unless the cognitive function test can be bypassed in some way, can be completed with assistance by some other mechanism, uses object recognition (such as "click on the photo of a flower"), or uses identification of non-text content provided by the the user (such as a user-provided image).

<br>

## Robust

Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.

> #### Guideline 4.1
>
> Maximize compatibility with current and future user agents, including assitive technologies.

#### 4.1.1 Parsing (Obsolete and removed) (A, 2.0)

NOTE: This success criterion is no longer useful and as of 2023 has been removed from WCAG. It previously required that significant HTML validation/parsing errors be avoided.

#### 4.1.2 Name, Role, Value (A, 2.0)

- Markup is used in a way that facilitates accessibility. This includes following the HTML specifications and using forms, input labels, frame titles, etc. appropriately.

- ARIA is used appropriately to enhance accessibility when HTML is not sufficient.

#### 4.1.3 Status Messages (AA, 2.1)

- If an important status message is presented and focus is not set to that , the message must be announced to screen reader users, typically via an ARIA alert or live region.message
