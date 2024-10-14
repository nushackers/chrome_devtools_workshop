---
theme: dracula
class: text-center
background: none
highlighter: shiki
lineNumbers: false
favicon: /quackers.png
info: |
  Hacker Tools 24/25 - Chrome Devtools
drawings:
  persist: false
download: true
transition: fade
title: "Hackertools: Chrome Devtools"
mdc: true
fonts:
  sans: "Inter Tight"
  serif: "Inter Tight"
  mono: "Jetbrains Mono"
layout: center
---

# HackerTools: Chrome Devtools

<img src="/devtools-logo.png" class="ml-30 mt-10 h-60" />

---
layout: center
---

# Slides

[**https://nushackers.github.io/chrome_devtools_slides**](https://nushackers.github.io/chrome_devtools_slides)

<img src="/slides_link.png" class="ml-25 h-60" />

---
layout: center
---

Hi I'm **River**! My GitHub is: https://github.com/oceankoh/

* I'm a Y2 CS undergraduate
* Used to do quite a bit of frontend development 
* Compete in CTFs with NUS Greyhats specialising in web security 

---
layout: center
---

# Prerequisites

* Google Chrome 
  * Although other browsers should have similar developer features
* **Basic** HTML/CSS/Javascript knowledge

---
layout: center
---

# [Official Chrome Devtools Documentation](https://developer.chrome.com/docs/devtools/)

---
layout: center
---

## Contents we'll be covering today

* Understanding what a browser is
* Overview of devtools
* Inspect Elements
* Working with the Console 
* Debugging client-side Javascript
* Viewing network requests

---
layout: center
---
## What is a (Web) Browser?

A browser is an application that:

- **Requests and renders web pages** from the internet.
- Manages **HTML, CSS, and JavaScript** to create interactive experiences.

Modern browsers, like Chrome, have tools that help developers inspect and optimize the pages they build.

---
layout: center
---

## Overview of DevTools

DevTools is built directly in the browser and allows you to edit pages on-the-fly and diagnose problems quickly. Some features include:

- **Inspect HTML and CSS** to understand how a webpage is built.
- **Debug JavaScript** to find and fix errors in code execution.
- **Monitor network traffic** to see all files and resources a page loads.
- Optimize performance and improve **user experience** by analyzing load times.

---
layout: center
---
# Opening Devtools
## Mouse

Open Elements Panel: `Right Click -> Inspect`

## Shorcuts
|OS|Elements|Console|Last Panel|
|:---|:---|:---|:---|
|Windows / Linux|`Ctrl + Shift + C`|`Ctrl + Shift + J` |`F12` <br> `Ctrl + Shift + I`|
|Mac|	`Cmd + Option + C`|	`Cmd + Option + J`|	`Fn + F12` <br> `Cmd + Option + I`|

---
layout: center
---

## Key Panels:

1. **Elements:** View and modify HTML & CSS.
2. **Console:** Run JavaScript commands and see log messages.
3. **Sources:** View website's resources and debug Javascript.
4. **Network:** Track requests made by the browser.


---
layout: center
---

# Inspect Elements

The **Elements panel** allows you to:
- **Edit ~~HTML~~ the DOM** and see changes in real-time.
- See the **CSS rules applied** to each element.
- Modify styles on the fly to experiment with layout and design.

This is especially useful for:

- **Fixing layout bugs.**
- Identifying **styling issues**.
- Quickly testing visual changes.

---
layout: default
---
# Let's try it out

## [DOM Exercise](https://developer.chrome.com/docs/devtools/dom)  

<br>

## [CSS Exercise](https://developer.chrome.com/docs/devtools/css)

---
layout: center
---

## Working with the Console

The **Console tab** is a powerful tool for debugging and testing JavaScript in real time:

- Output **log messages** and track interactions.
- Test JavaScript by typing commands directly into the console.
- View **warnings** and **error messages** to diagnose problems with your script.
- Use **console functions** like `console.log()`, `console.error()`, and `console.table()` to display information during runtime.

### Use Cases:

- **Live testing:** Execute small snippets of code directly in the browser.
- **Debugging:** Check variable values and identify script errors.
- **Handling Errors:** Capture and display errors and warnings in your code.

---
layout: default
---

# Let's try it out
## [`console.log()` demo](https://devtools.glitch.me/console/log.html)

---
layout: center
---

## Debugging Client-side JavaScript

The **Sources tab** provides tools to:

- Set **breakpoints** to pause the execution of your code at specific lines.
- Step through code **line by line** to trace the execution flow.
- Inspect the value of **variables and expressions** at runtime.
- Use **conditional breakpoints** to pause execution only when a specific condition is met.

This helps in:

- Understanding **complex logic**.
- Identifying why **unexpected behavior** occurs.
- **Fixing bugs** without needing to rely solely on `console.log()`.

---
layout: default
---

# Let's Try it out!
## [`Simple Password Checker` Exercise](https://web.for.idiot.sg/final-section-lets-get-flag-8008.html)  

<br> 

## [`Harder Password Checker` Exercise](https://oceankoh.github.io/reversing-with-devtools/)


---
layout: center
---

## Viewing Network Requests

The **Network tab** tracks all network activity between the browser and server, including:

- **HTTP requests** and responses (status codes, headers, etc.).
- **Load times** for all assets (HTML, CSS, JavaScript, images).
- The **size** of resources and how long each took to download.
- **Filtering** by specific request types (e.g., XHR for AJAX calls).
- Monitoring **API requests**, payloads, and responses for debugging client-server interactions.

This is especially useful for:

- Identifying **bottlenecks** in page load performance.
- Troubleshooting **API requests** that may be failing or slow.
- Seeing which resources might be **blocking rendering**.

---
layout: center
---

# Let's Try it out!
## Can you answer these questions about [`NUSMods](https://nusmods.com)

* What (deprecated) service/APIs does the NUSMods site query?
* When are these network requests made?
* Can you identify the function that performs the request?


---
layout: center
---

# And that's it!

---
layout: center
---

## Feedback Form

Let us know your thoughts on this workshop!

<img src="/feedback.png" class="m-10 h-60" />

---
layout: cover
background: none
---

# What's next?

