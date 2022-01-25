
# Website Accessibility

Accessibility is to ensure a positive user experience (UX) for people without and with disabilities such as sight, hearing, and speech, neurological conditions and low internet quality [(HostingCanada)](https://hostingcanada.org/canadian-website-accessibility-guidelines/). 

[Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/2018/REC-WCAG21-20180605/) is broad ranging recommendations to make the internet more accessible. There are two streams of recommendations, one for persons with disabilities and the other is regarding accessibility of web content, such as devices used. 


**Guidelines** - The 13 guidelines provide the basic goals that authors should work toward in order to make content more accessible to users with different disabilities.


**Success Criteria** In order to meet the needs of different groups and different situations, three levels of conformance are defined: 
- A (lowest), AA, and AAA (highest). 
- Additional information on WCAG levels can be found in [Understanding Levels of Conformance.](https://www.w3.org/WAI/WCAG21/Understanding/conformance#levels)



---
# Quick Guide to Meet WCAG

## Principle 1 - Perceivable

The information must be presentable to users in ways they can perceive. 

### Guideline 1.1 - Text Alternatives

Provide text alternatives for any non-text content so that it can be changed into other forms people need, such as large print, braille, speech, symbols or simpler language.

- quick wins: use Alt Text for ASCII art, emoticons, leetspeak, img elements, button descriptions


### Guideline 1.2 - Time based Media

For pre-recorded media (audio and video) ensure that the information is equivalent to the Alt text

- Captions: provide open and visible captions. Omitting dialogue or important sound effects is a *fail*
- Audio descriptions: when a lecturer says "this code block/ item" provide an audio description of what *this* is to those who cannot see
- Sign language: include a sign language interpreter in the video stream


### Guideline 1.3 - Adaptable

Program information into the HTML or other code into your works, such as 
**(ARIA)** Accessible Rich Internet Applications [documentation link](https://www.w3.org/TR/wai-aria/) for describing a landmark or specific text element.

ARIA HTML Tutorial by Gary Simon
- https://youtu.be/0hqhAIjE_8I

**Sensory information**
- Providing an action button labelled 'go' and instructions "to submit the form press the round button labelled go". This provides shape and textual information to local the button.

**Input fields**
- Input fields with purposeful information


### Guideline 1.4 - Distinguishable

Make it easier for users to see and hear content including separating foreground from background.

- control audio that plays automatically, failure to do so can mean the entire webpage or content can be interfered with

- contrast of text and images, strive for a contrast ratio of 4.5:1. Background color is solid (black or white), CSS font size between 14pt and 18pt (18.5px and 24px)

- resize text (excluding caption and image text)

- low or no background audio (*super helpful!*)

- visual presentation: the foreground and background colors can be selected by the user, text is not justified, line spacing is space-and-a-half, text can be resized up to 200 percent

- images of text are used for pure decoration

- non-text contrast, visual presentation should have a contrast ratio or more of 3:1

- hover content, when a pointer or keyboard focus triggers additional content make it dismissible or persistent until the user dismissed it



# Principle 2

User interface components and navigation must be operable.

## Guideline 2.1 - Keyboard Accessible

make all functionality available from a keyboard (mouse input in addition) and ***avoid making a keyboard trap*** where the user cannot escape the interface with a keyboard.

- turn off or allow user to turn off keyboard shortcuts

## Guideline 2.2 - Enough time

Provide users enough time to read and use content

- allow user to turn off time limit before encountering it or allow adjustment with extending the expiration time. A time limit longer than 20 hours. 

- pause, stop, auto-updating & hide information. Give the suer enough time to interact with content by pausing and stopping information. Flash and animations should be limited in use.

- no timing (*easy win!*), timing is not essential to the event or activity

- interruptions should be suppressed/ postponed by the user (except for emergencies)

- re-authenticating, when session expires and user does not lose information or data after authentication

- timeouts (*easy win*), warn users of the duration of any inactivity that could cause the loss of data or information



## Guideline 2.3 - Flashes & Seizures

try to avoid web content that flashes more than 3 times.



## Guideline 2.4 - Navigable 

Provide ways to help users navigate, find content, and determine where they are.

- provide bypass blocks or skip buttons 
- have a page titled that describes topic or purpose (*easy win!*)
- have content in a logical flow and focused manner
- provide link text that describes purpose of link or elements
- provide more than one link
- headings and labels that describe topic or purpose (*easy win!*)
- provide HTML breadcrumbs so the user knows where they are located on content
- section headings, use section heading to organize content



## Guideline 2.5 - Input Modalities

Make it easier for users to operate functionality through various inputs beyond keyboard.

- pointer gestures (do not rely on path-based gestures)
- pointer cancellation : no down event, abort or undo, up reversal. Allow drag & drop actions to be cancelled
- properly use the name in the label and text in label or image text
- target size for pointer input is at least 44px in CSS




## Principle 3 - Understandable

Information and the operation of the user interface must be understandable.

## Guideline 3.1 - readable

Make text content readable and understandable.

- properly use human language on the page
- provide definitions of words or phrases in a glossary with link element 
- provide the expansion or explanation of an abbreviation
- text should be at lower secondary education level when not technical
- pronunciation of a word in text and/or in audio format


## Guideline 3.2 - Predictable

Make your content predictable without any suprises. 

- have an input button with select element
- provide submit buttons with form action in PDF forms
- describe what will happen before a change will take place
- have consistent navigation
- have consistent web page elements and functions identified
- provide an update action call instead of automatic updating


## Guideline 3.3 - Input Assistance

Help users avoid and correct mistakes.

- provide error identification, text descriptions to identify required fields
- use ARIA invalid to indicate error field
- labels or instructions provided when content requires user input, using ARIA for descriptions (*easy win!*)
- provide text descriptions to identify errors, error suggestion, input error 
- for legal or financial information, provide reversible submisison, the user input is checked for input errors and confirm information before submission

provide help link on every web page























