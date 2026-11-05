---
name: yila-task
description: Hand a whole research job to Yila's own research agent and bring back its answer and files. Use when the user wants a deep literature search, a full literature review with real citations, a slide deck (PPTX), an academic poster, a data analysis report, or a manuscript section polished or translated, and wants Yila to do the work.
---

# Hand a job to Yila

`yila_run_task` starts an ordinary Yila task in the user's account. Yila's research agent works on it with its own sources, sandbox and skills, and the task appears in the user's Yila task list. The tool schemas are authoritative; this skill adds how to use them well.

## Start

- Use it for multi-step work: a deep search, a literature review, a deck, a poster, a data analysis, polishing or translating. For one quick search, one reference check or one figure, use the quick tools instead (`yila_search_papers`, `yila_verify_references`, `yila_figure_create`).
- Write `request` so it stands alone, because Yila cannot see this conversation. Say what to produce, the subject, the scope, the format, the length and the language. Include the facts and links Yila needs. Add "Do not ask me questions; go ahead." when the user wants no questions.
- `max_credits` is a hard cap for the whole task, follow-ups included (at least 100). Typical costs: a deep search or a review 300–2,000; a deck or a poster 500–3,000. Ask the user before choosing a large cap. The task is billed by actual usage and pauses at the cap; the user can raise the cap on the Yila website.
- Use a new `idempotency_key` for each new task. After a timeout, check `yila_job_list` instead of starting again.

## Wait

- Tell the user the task is running; long tasks take 5–30 minutes. Wait with `yila_job_status` (`wait_seconds` 20). Never start the task again because it is slow.
- `done`: relay Yila's reply and list its files with their download links. Links expire in 15 minutes. Downloading documents needs a paid Yila plan; otherwise the user opens the task page.
- `needs_input`: Yila asked a question. Show it to the user, then open the task page with `yila_open_in_browser` (`project_id` = the task id) so the user answers there. Then keep waiting.
- `paused_credits`: the task reached its cap or the balance ran out. Tell the user; they raise the cap or top up on the Yila website.

## Continue

- `yila_task_reply` sends the next message in the same task (a change, a shorter version, the next step), within the same cap. Then wait again.

## Rules

- Relay only what Yila returned. Never invent results, references or files.
- Do not start a task the user did not ask for; a task spends Yila credits.
