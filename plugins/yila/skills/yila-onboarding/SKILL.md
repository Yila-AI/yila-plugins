---
name: yila-onboarding
description: Connect to Yila and introduce what it can do. Use when the user installs or first mentions the Yila plugin, asks what Yila can do, or when the Yila tools have not been used yet in this conversation.
---

# Start with Yila

Use only this plugin's `yila` MCP connection. If its tools are missing because the connection is not authorized yet, start the host's own sign-in flow for the `yila` server and wait for the user to approve it in the browser. Never ask the user for a password, an API key or a token.

## First call

Call `yila_get_orientation` once per conversation before any other Yila tool. It returns the connected Yila account, its credit balance, the user's recent Yila projects and the manual: which tool to use when, what costs credits and how to open the Yila canvas. Follow it. If the connection is refused, run the sign-in flow again.

## Introduce Yila

Introduce Yila in the user's language, briefly, and invent nothing:

- **Scientific figures with the canvas beside the chat.** Yila draws publication-quality figures (graphical abstracts, mechanism diagrams, workflows) from the outline you write after reading the user's paper or notes. The figures are saved in the user's Yila project, and the editable Yila canvas opens in the host's built-in browser, already signed in. The user can paste an advisor's or reviewer's comments and get a new version next to the old one, then export editable PPTX or SVG on the canvas.
- **Literature, checked and cited.** Search OpenAlex, PubMed, Google Scholar and Wanfang (Chinese) with citation keys and abstracts; turn DOIs, titles or a pasted reference list into exact records; format references in 2,800+ styles including GB/T 7714; check a draft's references for wrong details or entries that do not exist; save papers to the user's Yila library and notes to the project.
- **Whole jobs handed to Yila.** A deep literature search or a full review with real citations, a slide deck, an academic poster, a data analysis: Yila's own research agent runs it in the user's account (it shows in their Yila task list) and returns its answer and files.
- **Not yet through the plugin:** uploading the user's own files for Yila to read; that runs in the Yila web app.

Then offer two starter requests that fit the user's field, for example:

- "Read the attached paper and draw a 16:9 graphical abstract with Yila."
- "Revise this figure with Yila from my advisor's comments: …"
- "Use Yila to find recent papers on <topic> and check every reference in my draft."
- "Have Yila write a literature review on <topic> with real citations, at most 1,000 credits."

Do not start a paid action (a figure, an edit, a search, a reference check, a task) during onboarding unless the user asked for one. Mention that these use Yila credits (a figure usually 300, a search 30 per source that returns papers, a reference check 10 each, a task by actual usage up to the cap you set) and that each result says what it charged.
