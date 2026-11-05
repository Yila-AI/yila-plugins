---
name: yila-canvas
description: Open a Yila project and its figure canvas in the host's built-in browser, or give the user a link to click. Use after a Yila figure is ready, or when the user wants to see or edit a Yila figure.
---

# Open the Yila canvas

## Open

Call `yila_open_in_browser` with the `figure_id` (or the `project_id`). It returns a link that signs the browser in to the user's Yila account once and opens the project's canvas at that figure, where every figure of the project is laid out. The link works once and expires in about 5 minutes.

- If the host has a built-in browser, open the link there.
- Otherwise give the link to the user right away and ask them to click it.
- Do not fetch the link with HTTP or shell tools: that uses it up without showing anything.
- If the page asks the user to sign in, the link expired or was already used: request a new one.

A canvas opened from that link keeps showing the project's new figures and revisions by itself and moves to each new one while it stays open. Open a new link only if the user closed it.

## "Change this one"

When the user points at a figure on the canvas ("this one", "the selected one"), read the page before editing. In the built-in browser, read the hidden element:

```
document.getElementById("yila-agent-state").textContent
```

It is JSON: `project`, `selected` (the figure the user selected or enlarged: `figure` id, `title`, `isLatest`), `latest` and `figures` (all figures on the canvas, newest last). Each figure on the canvas also carries its id in `data-yila-figure-id`. Edit that figure with `yila_figure_edit`.

If you cannot read the page, use the figure you just made or revised, or one from `yila_job_list`, only when it is clearly the one the user means; otherwise ask. Do not guess.

## What stays on the canvas

Manual edits, element-level editing, comparing versions and exporting editable PPTX or SVG happen on the canvas. Point the user there rather than recreating these in the conversation.
