---
name: yila-canvas
description: Open a Yila project and its figure canvas in the host's built-in browser, or give the user a link to click. Use after a Yila figure is ready, or when the user wants to see or edit a Yila figure.
---

# Open the Yila canvas

## Open

Call `yila_open_in_browser` with the `figure_id` (or the `project_id`). It returns a link that signs the browser in to the user's Yila account once and opens the project's canvas, where every figure of the project is laid out. The link works once and expires in about 5 minutes.

- If the host has a built-in browser, open the link there.
- Otherwise give the link to the user right away and ask them to click it.
- Do not fetch the link with HTTP or shell tools: that uses it up without showing anything.
- If the page asks the user to sign in, the link expired or was already used: request a new one.

After every new figure or revision, open a new link: a page that is already open does not refresh by itself.

## "Change this one"

Use the `figure_id` of the figure the user means: the one you just made or revised, or one from `yila_job_list`. If it is unclear which figure they mean, ask; do not guess.

## What stays on the canvas

Manual edits, element-level editing, comparing versions and exporting editable PPTX or SVG happen on the canvas. Point the user there rather than recreating these in the conversation.
