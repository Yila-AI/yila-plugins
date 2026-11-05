---
name: yila
description: Yila 科研助手：画科研图并在画布上接着改，查中英文文献、核验引用、排参考文献。Use to draw scientific figures and to search, check and format literature with Yila.
---

# Yila

Call `yila_get_orientation` once before other Yila tools; it returns the connected account, the credit balance and how to use each tool.

- Figures: `yila_open_project` once per conversation, then `yila_figure_create` with a specific outline taken only from the user's material, a new `idempotency_key` and `max_credits` (usually 300). To revise, `yila_figure_edit` with the user's comments as written.
- A figure takes 1.5–3 minutes: wait with `yila_job_status` (`wait_seconds` 20, `status_only` true); each call returns within about 20 seconds. Never resubmit with a new `idempotency_key` because of a timeout; use `yila_job_list` to find a lost job.
- To show a figure, call `yila_open_in_browser` and give the user the link to click right away (it works once and expires in about 5 minutes); `yila_figure_preview` gives a download link.
- Errors: `QUOTE_EXCEEDS_MAX_CREDITS` → ask the user before raising `max_credits`; `INSUFFICIENT_CREDITS` → tell the user the balance and the plans link; `RATE_LIMITED` → wait for a running job to finish.
- Literature: `yila_search_papers` (write the queries yourself; English for OpenAlex/PubMed/Google Scholar, Chinese concept groups for Wanfang; 30 credits per source that returns papers; page with offset and the same idempotency_key), `yila_lookup_papers` (DOIs, titles or a pasted list → CSL records, free), `yila_format_references` (GB/T 7714 by default for Chinese, free), `yila_verify_references` (10 credits each), `yila_library`, `yila_save_note`.
- Never invent results or references; cite only what Yila returned or the user gave you.
