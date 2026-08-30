---
title: Design Mode
source: https://www.onorca.dev/docs/browser/design-mode
---

Design Mode transforms the Orca browser into a pointer-to-code tool. By enabling it, you can click any UI element on the rendered page, and that element appears in the agent chat as rich context — complete with its DOM, computed styles, and a screenshot.

![Design Mode: click a button, it lands in the agent chat](/whats-new/posters/orca-design-mode.jpg)

## Turn it on

Access the **Design Mode** toggle in the browser toolbar. Once activated, your cursor transforms into a picker that highlights elements as you hover over them.

## Drop into chat

When you click an element, Orca captures several pieces of information:

* The element's HTML, including outer structure and surrounding context
* Its computed CSS properties — including colors, fonts, and spacing
* A cropped screenshot of the element
* The source file and line number, if a dev-mode source map exists

This information is sent to the active agent terminal as a single attachment, allowing you to describe your desired changes.

## Use the result

The agent modifies the source code, Orca refreshes the preview automatically, and you can click again to verify the changes. The most streamlined version of this workflow is detailed in the recipe titled "Fix a UI bug with Design Mode."
