---
name: yila
description: Yila 科研画图：根据论文画图形摘要、机制图、流程图，在 Yila 画布上接着改。Use to draw and revise scientific figures with Yila.
---

# Yila

Call `yila_get_orientation` once before other Yila tools; it returns the connected account, the credit balance and how to use each tool.

- Figures: `yila_open_project` once per conversation, then `yila_figure_create` with a specific outline taken only from the user's material, a new `idempotency_key` and `max_credits` (usually 300). To revise, `yila_figure_edit` with the user's comments as written.
- A figure takes 1.5–3 minutes: wait with `yila_job_status` (`wait_seconds` 20, `status_only` true); each call returns within about 20 seconds. Never resubmit with a new `idempotency_key` because of a timeout; use `yila_job_list` to find a lost job.
- To show a figure, call `yila_open_in_browser` and give the user the link to click right away (it works once and expires in about 5 minutes); `yila_figure_preview` gives a download link.
- Errors: `QUOTE_EXCEEDS_MAX_CREDITS` → ask the user before raising `max_credits`; `INSUFFICIENT_CREDITS` → tell the user the balance and the plans link; `RATE_LIMITED` → wait for a running job to finish.
- Literature search, reading and reference tools are coming soon; do not offer them yet. Never invent results or references.
