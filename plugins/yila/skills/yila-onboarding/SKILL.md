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
- **Not yet through the plugin:** deep multi-step search and full-text reading; they run in the Yila web app.

Then offer two starter requests that fit the user's field, for example:

- "Read the attached paper and draw a 16:9 graphical abstract with Yila."
- "Revise this figure with Yila from my advisor's comments: …"
- "Use Yila to find recent papers on <topic> and check every reference in my draft."

Do not start a paid action (a figure, an edit, a search, a reference check) during onboarding unless the user asked for one. Mention that these use Yila credits (a figure usually 300, a search 30 per source that returns papers, a reference check 10 each) and that each result says what it charged.
