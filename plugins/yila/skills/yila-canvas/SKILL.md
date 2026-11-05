---
name: yila-canvas
description: Open a Yila project, canvas or figure in the host's built-in browser and work with what the user selected on it. Use after a Yila figure is ready, when the user wants to see or edit a figure, or when the user says "change this one" while the Yila canvas is open.
---

# Open the Yila canvas

## Open or refresh

Call `yila_open_in_browser` with the project (and the figure, when there is one). It returns a link that signs the browser in once and expires in about 5 minutes.

- Open the link in the host's built-in browser if the host has one. If the canvas is already open, refresh it instead of opening a second page.
- **Never show this link in your reply, and never store it.** It signs in as the user. If the host has no browser, call `yila_open_in_browser` again and tell the user to open the new link themselves, right away.
- If the page asks the user to sign in, the link has expired or was already used: request a new one.

## "Change this one"

When the user points at something on the canvas, read the hidden state element before editing:

```
document.getElementById("yila-agent-state").textContent
```

It is JSON: the project, the selected figures (id, version, title) and the latest figure. Edit the selected figure with `yila_figure_edit`. If you cannot read the page, ask the user which figure they mean; do not guess.

## What stays on the canvas

Manual edits, element-level SVG editing, comparing versions and exporting editable PPTX or SVG all happen on the canvas. Point the user there rather than recreating these in the conversation.
