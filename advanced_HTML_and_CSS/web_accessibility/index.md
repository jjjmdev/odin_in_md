# [Introduction to Web Accessibility](https://www.theodinproject.com/lessons/node-path-advanced-html-and-css-introduction-to-web-accessibility)

## Introduction

At this point in the curriculum you've learned incredibly valuable concepts in whichever full stack path you chose, you've created some awesome, resume-worthy projects, and you should have a better understanding of some HTML and CSS concepts. One could even argue that you may now love working with CSS...?

What you may not have too much an understanding of, though, is the topic of accessibility, often referred to as "a11y" (due to there being 11 letters between the first and last letters). Unfortunately, this is a topic that many people either don't know much about, or just don't take into account when developing websites. If you fit into either of those two categories, you may have adopted some habits that aren't exactly a11y-friendly. Before we get into how you can break away from such habits and begin implementing a11y friendly concepts, it's important to first understand some basic information about web accessibility.

<br>

## Lesson overview

This section contains a general overview of topics that you will learn in this lesson.

- Explain what web accessibility is.

<br>

## What is web accessibility?

Web accessibility means that websites, tools, and techonologies are designed and developed so that people with disabilities and other circumstantial limitations can use them with as few barriers as possible.

There are different types of disabilities, including (but not limited to) auditory, physical/motor, cognitive, or visual. A disability can be permanent, such as a user who is completely blind or deaf, or it can be temporary, such as a user with a broken arm. Users can have multiple disabilities at any given time. Older users with changing abilities may even have similar conditions as those who have a disability.

Situational limitations are a little different. Using a phone outside on a bright day, browsing a site with one hand while you're busy doing something else with the other, or living in an area where the internet is slow or the bandwidth is expensive are all examples of situational limitations. These limitations, unlike a disability, occur to users only in specific situations, but are still important to keep in mind when developing a website.

<br>

## Why web accessibility matters

Let's first look at a non-web example to gain a little perspective. Imagine being in a multi-storied building that has no elevator. For some people, this might only be an annoyance. "Huh, no elevator. I guess I'll walk up a few flights of stairs, then." A person that requires a wheelchair, however, would find it impossible, or at the very least much more difficult, to go anywhere beyond the first floor. Even if a person in a wheelchair had someone to lift the wheelchair up each step, it would be a much more difficult process. The point here is that an elevator would have made this building more accessible.

The building is your website, and the elevator is a collection of various accessibily features and tools (...it's a pretty big elevator). When you develop a website, you're developing it for users, and you need that website to actually be _usable_ by them. People with disabilities, older people with changing abilities, people who aren't as tech savvy, and people with some sort of situational limitation are still users, and websites should be as equally usable by them as possible.

One other pretty big reason that accessbility matters is that, depending on the country, there could actually be laws _requiring_ accessibility to be implemented.

<br>

## Knowledge check

- ##### What is web accessibility?

Web accessibility means that websites, tools, and technologies are designed and developed so that people with disabilities and other circumstantial limitations can use them with as few barriers as possible.

<br>

- ##### Who truly benefits from accessibility features?

When you develop a website, you're developing it for users, and you need that website to actually be usable by them. People with disabilities, older people with changing abilities, people who aren't as tech savvy, and people with some sort of situational limitation are still users, and websites should be as equally usable by them as possible.

<hr>
<br>
<br>

# [Diverse Abilities and Barriers](https://www.w3.org/WAI/people-use-web/abilities-barriers/)

### _"Accessibility: It's about people"_

> ##### Summary
>
> This section explores the wide diversity of abilities. It highlights some accessibility barriers that people experience because of inaccessible digital technology. The examples given are not a complete list of all disabilities or barriers.

<br>

## Diverse abilities

There are many reasons why people may be experiencing varying degrees of auditory, cognitive, physical, speech, and visual disabilities. For instance, some may have disabilities from birth, an illness, disease, or accident, or they may develop impairments with age. Some may not consider themselves to have disabilities even if they do experience such functional limitations.

Each individual is unique. People have diverse abilities, skills, tools, preferences, and expectations that can impact how they use the digital technology. For instance, consider the following aspects:

- **Age-related impairments:** People with age-related impairments often have the same function requirements as other people with disabilities. However, their use of digital technology and adoption of assistive technologies may differ.

- **Multiple disabilities:** Some people have combinations of different kinds of disabilities, which may limit their approaches for interacting with digital technology. For example, someone who is deaf and has low vision might benefit from captions for audio, but only if these captions have adjustable size and color.

- **Health conditions:** Some people have health conditions that may affect their stamina, dexterity, or concentration. For instance, some may experience fatigue, pain, or other symptoms that could have an impact on their physical use of the computer or limit the duration or extent of their use of digital technology.

- **Changing abilities:** Some people may be experiencing progressive or recurring functional limitations that impact their use of digital technology differently at different times. For example, some may need particular accessibility features on one day, and others or none on another day, depending on their condition.

- **Temporary impairments:** Some people may be experiencing temporary impairments such as those that may occur due to an accident, surgery, or medication. They may not know about accessibility solutions, may not know how to use accessibility features, and may be unaware of their needs.

- **Situational limitations:** Some people may be experiencing constraints due to their surrounding or due to other situational aspects. For example, they may be in a loud environment and unable to hear audio, in bright sunlight and unable to see a screen, or they may not be able to afford some technologies.

Digital technology designed for people with a broad range of abilities benefits everyone, including people without disabilities. It is, therefore, important to consider the broad diversity of functional needs rather than categorize people according to medical classifications.

<br>

## [Auditory](https://www.w3.org/WAI/people-use-web/abilities-barriers/auditory/)

Auditory disabilities range from mild or moderate hearing loss in one or both ears ("hard of hearing") to substantial and uncorrectable hearing loss in both ears ("deafness"). Some people with auditory disabilities can hear sounds but sometimes not sufficiently to understand all speech, especially when there is background noise. This can include people using hearing aids.

### Introduction

While multimedia provides many opportunities for people with auditory disabilities, it also poses challenges when content is not designed to be accessible. For example, while video content can be used to commiunicate information visually, audio content needs to have alternatives, such as transcripts and captions, so that it is accessible for people with auditory disabilities.

To use multimedia, people with auditory disabilities often rely on:

- Transcripts and captions of audio content, including audio-only content and audio tracks in multimedia;

- Media players that display captions and provides options to adjust the text size and colors of captions;

- Options to stop, pause, and adjust the volume of audio content (independently of the system volume);

- High-quality foreground audio that is clearly distinguishable from any background noise.

For some people with auditory disabilities, sign language is the primary language, and they may not read the written language as fluently. Providing important information in sign language and using simpler text that is supplemented by images, graphs, and other illustrations help make digital content more understandable to many people. However, it is important to remember that not all people with auditory disabilities know sign language.

### Examples of auditory disabilities

- **Hard of hearing** - mild or moderate hearing impairments in one or both ears.

- **Deafness** - substantial, uncorrectable impairment of hearing in both ears.

- **Deaf-blindness** - substantial, uncorrectable hearing and visual impairments.

### Examples of barriers for people with auditory disabilities

- Audio content, such as videos with voices and sounds, without captions or transcripts.

- Media players that do not display captions and that do not provide volume controls.

- Media players that do not provide options to adjust the text size and colors for captions.

- Web-based services, including web applications, that rely on interaction using voice only.

- Lack of sign language to supplement important information and text that is difficult to read.

<br>

## [Cognitive and learning](https://www.w3.org/WAI/people-use-web/abilities-barriers/cognitive/)

Cognitive and learning disabilities affect how people store, retrieve, or use information. Often, only some functions are impaired while others are unaffected. Many of these disabilities do not affect overall intelligence. Cognitive and learning disabilities are usually invisible and can be age-related. Many users may not have a formal diagnosis or disclose having a disability due to social stigma, vocational concerns and prejudices. Poor design or content choice can undermine or make impossible these different approaches.

### Introduction

Cognitive and learning disabilities is an umbrella term for a large spectrum of differences and disabilities. They may affect the ability to:

- Learn, communicate, read, write, do math, or process sensory input;

- Understand or process new or complex information and learn new skills;

- Use memory and attention or visual, language, or numerical thinking.

Often, only some functions are impaired while other cognitive functions are unaffected. For example, someone with dyslexia may have trouble reading words but not math equations. Sometimes, cognitive and learning disabilities may include intellectual impairments that affect comprehension, alongside written and spoken expression. People may also experience more than one type of cognitive and learning disability. Note that the terminology and definitions used for cognitive and learning disabilities varies between countries.

Computer technologies provide many opportunities for people with cognitive and learning disabilities to interact with content and to process information in ways that are more usable to them. For example, people can navigate digital content using different strategies, access information in text, audio, or other formats, and change the presentation of the content according to their individual needs or preferences.

To use digital technology effectively, people with cognitive and learning disabilities often rely on:

- Clearly structured content that helps users focus and find what they need;

- Consistent labeling of forms, buttons, and other content parts so that useres understand what they are being asked to do;

- Predictable link targets, functionality, and overall interaction;

- Different ways of navigating websites, such as hierarchical menus and search;

- Options to suppress blinking, flickering, flashing, and continually changing content;

- Clear content with simple words, short sentences, short blocks of text that is supported by images, graphs, and other illustrations.

- Designs that make errors less likely and that make it easy for users to correct errors.

People with cognitive and learning disabilities may use different types of browsing methods or tools to support their particular needs. For example, spell checkers to help when filling in forms, passwords management tools, and text-to-speech with synchronized highlighting of the phrase being read. Some people use tools that resize text and spacing or customize colors to assist reading. Others may require alternative presentation of content, such as additional symbols or simplification. For these methods to work, developers need to make products that support adaptation and personalization.

## Examples of cognitive and learning disabilities

- **Age-related forgetfulness** (sometimes called "age-appropriate forgetfulness" or "age-related memory loss") - impaired memory that can be a normal part of healthy aging, such as taking longer to learn new things and occasionally forget particular words.

- **Attention deficit hyperactivity disorder (ADHD)** (formerly "attention deficit disorder (ADD)") - involves difficulty focusing on a single task, focusing for longer periods, or being easily distracted.

- **Autism spectrum disorder (ADS)** (includes "autism", "Asperger syndrome", and "pervasive developmental disorder (PDD)") - involves impairments of social communication and interaction abilities, and sometimes restricted habits and interests.

- **Brain injury** (traumatic or acquired) - damage that can happen at any stage in life and can lead to long-term impairment of executive function, memory, learning, coordination, speech, and emotions as well as other physical and sensory impairments.

- **Dementia** - includes memory loss and trouble concentrating, following a conversation, and finding the right word.

- **Dyslexia** - learning disability best known for its effect on the development of literacy and language-related skills

- **Intellectual disabilities** (called "learning disabilities" or "developmental disabilities" in some areas) - involves impairments of intelligence, learning more slowly, or difficulty understanding complex concepts.

- **Learning disabilities** - a general term used to describe difficulty learning new concepts. In Europe and some other countries, it refers to intellectual disabilities.

- **Mild cognitive impairment (MCI)** - sometimes considered the stage between age-related forgetfulness and the more serious decline of dementia.

- **Mental health disabilities** - includes disabilities that interfere with daily functioning due to challenges with self-regulation of emotions and thoughts. Examples include depression, anxiety, and post-traumatic stress disorder. These conditions may cause temporary or long-term challenges with accessing information, such as difficulty focusing on information, processing information, or understanding it.

- **Multiple sclerosis** - causes damage to nerve cells in the brain and spinal cord, and can affect cognitive, physical, and visual abilities, in particular during relapses.

### Examples of barriers for people with cognitive and learning disabilities.

- Complex, multi-stage process such as forms.

- Complex or inconsistent navigation mechanisms and page layouts that are difficult to understand and use.

- Complex sentences that are difficult to read and unusual words that are difficult to understand.

- Metaphors and other non-literal text whose meaning is not predictable from the usual meanings of the words.

- Long passages of text without images, graphs, or other illustrations to highlight the context.

- Moving, blinking, or flickering content, and background audio that cannot be turned off.

- Passwords and access codes that rely on memory.

- Time-outs on activities.

- Web browsers and media players that do not provide mechanisms to suppress animations and audio.

- Visual page designs that cannot be adapted using web browser controls or custom style sheets.

<br>

## [Physical](https://www.w3.org/WAI/people-use-web/abilities-barriers/physical/)

Physical disabilities (sometimes called "motor disabilities") include weakness and limitations of muscular control (such as involuntary movements including tremors, lack of coordination, or paralysis), limitations of sensation, joint disorders (such as arthritis), pain that impedes movement, and missing limbs.

### Introduction

To use digital technology, people with physical disabilities often use specialized hardware and software such as:

- Ergonomic or specially designed keyboard or mouse;

- Head pointer, mouth stick, and other aids to help with typing;

- On-screen keyboard with trackball, joysticks, or other pointing devices;

- Switches operated by foot, shoulder, sip-and-puff, or other movements;

- Speech recognition, eye tracking, and other approaches for hands-free interaction.

People with physical disabilities may be using a mouse or mouse-like device only, or keyboard or keyboard-like device only to operate the computer. People with physical disabilities rely on keyboard support to activate functionality provided on web pages. They may need more time to type, click, or carry out other interactions, and they may type single keystrokes in sequence or use sticky keys rather than typing simultaneous keystrokes ("chording") to activate commands. Such keystrokes include commands for special characters, shortcut keys, and to activate menu items.

People with physical disabilities may have trouble clicking small areas and are more likely to make mistakes in typing and clicking. Providing large clickable areas, enough time to complete tasks, and error correction options for forms are important design aspects. Other important design aspects include providing visible indicators of the current focus, and mechanisms to skip over blocks, such as over page headers or navigation bars. People with cognitive and visual disabilities share many of these requirements.

### Examples of physical disabilities

- **Amputation:** includes missing fingers, limbs, or others parts of the human body.

- **Arthritis** (previously called "rheumatism"): inflammation, degeneration, or damage to the joints.

- **Fibromyalgia** (formerly called "rheumatism"): the chronic pain of muscle and connective tissue.

- **Rheumatism**: typically refers to arthritis and other causes of bone or joint paint, and sometimes to fibromyalgia and other causes for muscular and other soft tissue pain.

- **Reduced dexterity**: is a functional term (rather than a medical condition) that describes the ability to control the hand, such as hand-eye coordination of people with cognitive and neurological disabilities.

- **Multiple sclerosis**: causes damage to nerve cells in the brain and spinal cord, and can affect physical, cognitive, and visual abilities, in particular during relapses.

- **Muscular dystrophy**: progressive weakness and degeneration of muscles, sometimes including in arms and hands.

- **Repetitive stress injury (RSI)** (also called "repetitive motion disorder" (RMD) and "cumulative trauma disorder" (CT)): involves injuries to the muscoskeletal system (bones, joints, tendons, and other connective tissues) and the nervous system from repetitive tasks and damage.

- **Tremor and spasms**: involuntary movement or muscle contraction, incluing short twitches, and continual or rhythmic muscle contractions.

- **Quadriplegia** (sometimes called "tetraplegia"): partial or total paralysis (includes motor control and sensation) to all four body limbs (legs and arms) and the torso.

- **Seizure disorders**: includes different types of epilepsy and migraines, which may be in reaction to visual flickering or audio signals at certain frequencies or patterns.

### Examples of barriers for people with physical disabilities

- Websites, web browsers, and authoring tools that do not provide full keyboard support.

- Insufficient time limits to respond or to complete tasks, such as to fill out online forms.

- Controls, including links with images of text, that do not have equivalent text alternatives.

- Missing visual and non-visual orientation cues, page structure, and other navigational aids.

- Inconsistent, unpredictable, and overly complicated navigation mechanisms and page functions.

<br>

## [Speech](https://www.w3.org/WAI/people-use-web/abilities-barriers/speech/)

Speech disabilities include difficulty producing speech that is recognizable by others or by speech recognition software. For example, the loudness or clarity of someone's voice might be difficult to understand.

### Introduction

People with speech disabilities encounter barriers with voice-based services, such as automated hotlines and applications that are operated using voice commands. To use services that rely on voice, people with speech disabilities need alternative modes of interaction such as text-based chat to interact with hotline representatives. Also, when the telephone numbers is the only means of communicating with an organization, it poses barriers for people with speech disabilities. Alternative means of communication include e-mail and feedbac forms.

### Examples of speech disabilities

- **Apraxia of speech (AOS)**: includes inconsistent articulation and production of speech sounds, and errors producing sounds in the correct order so that spoken words of phrases become difficult to understand.

- **Cluttering** (also called "tachyphemia"): includes increased speaking rate, incorrect rhythm, intonation, and co-articulation of sounds, and other influent speech that is sometimes similar to stuttering.

- **Dysarthria**: involves weakness or complete paralysis of muscles that are necessary to produce speech, including lips, lungs, throat, tongue, and others.

- **Speech sound disorder**: involves difficulty or inability to produce certain sounds or patterns of sound and sometimes results in addition, distortion, omission, or substitution of such sounds with others.

- **Stuttering**: includes influent speech, repetition of individual sounds or entire words and phrases, and misplacement or prolongation of pauses and sounds while speaking that is different from cluttering.

- **Muteness** (also called "mutism"): involves the inability to speak due to various reasons such as anxiety, brain injuries, or inability to hear and learn speech.

<br>

## [Visual](https://www.w3.org/WAI/people-use-web/abilities-barriers/visual/)

Visual disabilities range from mild or moderate vision loss in one or both eyes ("low vision") to substantial vision loss in both eyes ("blindness"). Some people have reduced or lack of sensitivity to certain colors (often called "color blindness"), or increased sensitivity to bright colors. These variations in perception of colors and brightness can be independent of the visual acuity.

### Introduction

People with visual disabilities typically rely on changing the presentation of digital technology into forms that are more usable for their particular needs. For example by:

- Enlarging or reducing text size and images;

- Customizing settings for fonts, colors, and spacing;

- Listening to text-to-speech synthesis of the content;

- Listening to audio descriptions of video in multimedia;

- Reading text using refreshable Braille.

For these browsing methods to work, developers should use style sheets to separate content from its presentation and correctly code the structure so that it can be processed and presented in different ways by browsers and assistive technologies. For example, some people do not see the content and rely on lists, headings, tables, and other page structures to be properly coded so that they can be identified by browsers and assistive technologies.

Some people are only seeing small portions of the content at a time or are perceiving the colors and design differently. Some people are using customized fonts, colors, and spacing to make the content more readable, or they are navigating through the content using keyboard only because they cannot see the mouse pointer. An accessible design supports different presentations of the digital content and different ways of interaction.

### Examples of visual disabilities

- **Color vision deficiency**: includes difficulty distinguishing between colors such as between red and green, or between yellow and blue, and sometimes inability to perceive any color (often called "color blindness").

- **Low vision**: (in some regions also called "partial sight") includes:

  - Vision that is not sharp or clear (low visual acuity)

  - Intolerance to light (photophobia or light sensitivity)

  - Inability to distinguish bright and dim areas of images or text against a background (contrast sensitivity)

  - Inability to obtain information when looking straight ahead (field of vision loss; can be central, peripheral, or scattered)

- **Blindness**: substantial, uncorrectable loss of vission in both eyes.

- **Deaf-blindness**: substantial, uncorrectable visual and hearing impairments.

### Examples of barriers for people with visual disabilities

- Images, controls, and other structural elements that do not have equivalent text alternatives.

- Text, images, and page layouts that cannot be resized, or that lose information when resized.

- Missing visual and non-visual orientation cues, page structure, and other navigational aids.

- Video content that does not have text or audio alternatives, or an audio-description track.

- Inconsistent, unpredictable, and overly complicated navigation mechanisms and page functions.

- Text and images with insufficient contrast between foreground and background color combinations.

- Websites, web browsers, and authoring tools that do not support the use of custom color combinations.

- Websites, web browsers, and authoring tools that do not provide full keyboard support.
