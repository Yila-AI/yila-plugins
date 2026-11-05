---
name: yila-figure
description: Draw and revise scientific figures with Yila (graphical abstracts, mechanism diagrams, workflows, schematics). Use when the user asks for a scientific figure, or asks to revise a Yila figure from feedback.
---

# Draw and revise figures with Yila

Yila does the drawing. You do the reading and planning: read the user's paper or notes yourself, then hand Yila a specific outline. The tool schemas are authoritative; this skill only adds how to use them well.

## Create a figure

1. Call `yila_open_project` once per conversation (or reuse the `project_id` you already have), so every figure lands in one Yila project.
2. Call `yila_figure_create` with the figure type, a short title, the content outline (the elements, their labels and the relationships between them, taken only from the user's material), the style, and the size and resolution when the user named them. Never invent results, numbers, mechanisms, author names or logos. If the material does not support something the user asked for, say so instead of drawing it.
3. Pass a new random `idempotency_key` for each new figure, and `max_credits` (a figure usually costs 300 credits). If Yila returns a quote instead of starting, show the price and ask the user before calling again with a higher limit.

The call returns a `job_id` right away. Then follow **Waiting**.

## Revise from feedback

When the user pastes feedback (from an advisor, a reviewer or themselves), call `yila_figure_edit` with the `figure_id`, the feedback as written, a new `idempotency_key` and `max_credits`. The new version appears next to the old one on the canvas; the old one stays. If it is unclear which figure the user means, ask.

## Waiting

A figure usually takes 1.5 to 3 minutes.

- Call `yila_job_status` with `wait_seconds` 20; each call returns as soon as the job finishes, or after 20 seconds. Add `status_only` to save tokens.
- Tell the user once that the figure is being drawn; do not narrate every poll.
- If the job is still running after about 15 minutes, stop, tell the user, and point them to the Yila project, where it will appear.
- **Never resubmit with a new `idempotency_key` because of a timeout.** That would draw and charge twice. Use `yila_job_list` to find a job you lost track of.

## Deliver

When the job succeeds, open the canvas (see the `yila-canvas` skill) instead of pasting a large image into the chat. If the host has no built-in browser, give the user the `yila_open_in_browser` link to click, or `yila_figure_preview` for a download link.

Tell the user what the job charged. `yila_get_orientation` shows the current balance.

## Editable files

Element-level edits and editable PPTX and SVG exports happen on the Yila canvas. Tell the user where they are; do not rebuild the figure in another tool.
