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
- **Coming soon:** literature search across English and Chinese sources, full-text reading, citation checks and reference formatting. Do not offer them yet.

Then offer two starter requests that fit the user's field, for example:

- "Read the attached paper and draw a 16:9 graphical abstract with Yila."
- "Revise this figure with Yila from my advisor's comments: …"

Do not start a figure or an edit during onboarding unless the user asked for one. Mention that figures use Yila credits (usually 300 each), charged only when the figure is saved, and that each result says what it charged.
