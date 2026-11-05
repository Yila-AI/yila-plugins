---
name: yila-figure
description: Draw and revise scientific figures with Yila (graphical abstracts, mechanism diagrams, flowcharts, illustrations). Use when the user asks for a figure, asks to revise one from feedback, or asks for an editable PPTX or SVG of a figure.
---

# Draw and revise figures with Yila

Yila does the drawing. You do the reading and planning: read the user's paper or notes yourself, then hand Yila an outline.

## Create a figure

Call `yila_figure_create` with:

- `outline`: panels, labels, arrows and claims, taken only from the user's material. Never invent results, numbers, mechanisms, author names or institution logos. If the material does not support something the user asked for, say so instead of drawing it.
- `kind`: `graphical_abstract`, `mechanism`, `flowchart` or `illustration`.
- `aspect_ratio` and `resolution` when the user named them (journals often want 16:9 or 4:3, 2K).
- `project_id` of the current Yila project if there is one (from `yila_get_orientation` or `yila_open_project`).
- `idempotency_key`: a new random key for each new figure. Reuse the same key only when retrying the same request.
- `max_credits`: the price the user accepted. If Yila returns a quote instead of starting, show the price and ask the user.

The call returns a `job_id` at once. Then follow **Waiting**.

## Revise from feedback

When the user pastes feedback (from an advisor, a reviewer, themselves), call `yila_figure_edit` with the figure id, the whole feedback text, and a new `idempotency_key`. If the user selected a figure on the canvas, read the canvas state first (see the `yila-canvas` skill) and edit that figure. The new version appears next to the old one on the canvas; keep both.

## Waiting

Figures usually take 1.5 to 3 minutes.

- Call `yila_job_status` with `status_only=true`. Wait about 5 seconds between calls for the first 90 seconds, then about 10 seconds.
- Each call may wait up to 20 seconds on the server; that is normal.
- Tell the user it is in progress; do not go silent.
- If the job is still running after 15 minutes, stop polling, tell the user it is still running, and that it will appear in their Yila project.
- **Never resubmit with a new idempotency key because of a timeout.** That would charge twice. Use `yila_job_list` to find a job you lost track of.

## Deliver

When the job succeeds, open the figure on the Yila canvas (see the `yila-canvas` skill) instead of pasting a large image into the chat. If the host has no browser, give the user the link from `yila_open_in_browser`, or call `yila_figure_preview` for a small preview.

Report what was charged and the remaining balance, as returned by the tool.

## Editable files

Editable PPTX and SVG are exported on the Yila canvas (the Export menu). Tell the user where it is; do not try to rebuild the figure in another tool.
