---
theme: seriph
class: text-center
background: none
highlighter: shikiji
lineNumbers: false
favicon: /quackers.png
info: |
  Hacker School 23/24 - Docker
drawings:
  persist: false
download: true
transition: fade
title: "Hackerschool: Docker"
mdc: true
fonts:
  sans: "Inter Tight"
  serif: "Inter Tight"
  mono: "Jetbrains Mono"
layout: center
---

# Hackerschool:

<img src="/docker-logo.png" class="m-20 h-60" />

---
layout: center
---

# Slides

[https://nushackers.github.io/chrome_devtools_slides](https://nushackers.github.io/chrome_devtools_slides)

![slides_qr](/slides_link.png)

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

# Official Chrome Devtools Documentation

[`https://developer.chrome.com/docs/devtools/`](https://developer.chrome.com/docs/devtools/)

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

## Understanding What a Browser Is

A browser is an application that:

- **Requests and renders web pages** from the internet.
- Acts as the interface between **you and the web server**.
- Manages **HTML, CSS, and JavaScript** to create interactive experiences.

Modern browsers, like Chrome, have tools that help developers **inspect and optimize** the pages they build.

---
layout: center
---

## Overview of DevTools

DevTools is a set of **built-in debugging tools** in Chrome that allow you to:

- **Inspect HTML and CSS** to understand how a webpage is built.
- **Debug JavaScript** to find and fix errors in code execution.
- **Monitor network traffic** to see all files and resources a page loads.
- Optimize performance and improve **user experience** by analyzing load times.

### Key Panels:

1. **Elements:** View and modify HTML & CSS.
2. **Console:** Run JavaScript commands and see log messages.
3. **Network:** Track requests made by the browser.
4. **Sources:** Debug JavaScript.
5. **Performance:** Analyze runtime performance.
6. **Application:** Inspect storage, cookies, and cache.

---
layout: two-cols
class: px-5 self-center
---

## Inspect Elements

The **Elements panel** allows you to:

- **View and modify HTML** directly to see changes in real-time.
- See the **CSS rules applied** to each element.
- Modify styles on the fly to experiment with layout and design.
- **Analyze box models** for elements (e.g., padding, margin, borders).

This is especially useful for:

- **Fixing layout bugs.**
- Identifying **styling issues**.
- Quickly testing visual changes.

### How to Access:

Right-click any element on the page and select **"Inspect"**.

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
layout: two-cols
class: px-5 self-center
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

## Use Cases for Viewing Network Requests

- Check how many **third-party scripts** or resources are being loaded.
- Monitor how **caching** affects page performance.
- Debug issues with **AJAX** or **fetch** requests.

---
layout: center
---

# And that's it!

---
layout: center
---

## Feedback Form

Let us know your thoughts on this workshop!

<img src="/feedback.jpeg" class="m-10 h-60" />

---
layout: cover
background: none
---

# What's next?

