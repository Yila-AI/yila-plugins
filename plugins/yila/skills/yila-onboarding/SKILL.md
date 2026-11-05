---
name: yila-onboarding
description: Connect to Yila and introduce what it can do. Use when the user installs or first mentions the Yila plugin, asks what Yila can do, or when the Yila tools have not been used yet in this conversation.
---

# Start with Yila

Use only this plugin's `yila` MCP connection. If the tools are missing because the connection is not authorized yet, start the host's own sign-in flow for the `yila` server and wait for the user to approve it in the browser. Never ask the user for a password, an API key or a token.

## First call

Call `yila_get_orientation` once per conversation before any other Yila tool. It returns:

- the connected Yila account and its credit balance;
- the user's recent Yila projects (each project is a task in the user's Yila account, with its own canvas, papers and notes);
- when to use each tool, how to cite papers, and how to link the user back to the Yila web app.

Follow what it says. If it returns `NOT_AUTHORIZED`, run the sign-in flow again.

## Introduce Yila

Introduce Yila in the user's language, briefly, with these two parts and nothing invented:

1. **Figures with a canvas beside the chat.** Yila draws publication-ready scientific figures (graphical abstracts, mechanism diagrams, flowcharts) from the user's paper or notes. The editable Yila canvas opens beside the conversation. The user can paste reviewer or advisor feedback and get a new version next to the old one, then export editable PPTX or SVG.
2. **A research workbench behind the agent.** Deep literature search across English and Chinese sources (including Wanfang), full-text reading with page citations, reference verification (real, mismatched or not found), references in 2,800+ styles including GB/T 7714, and a library and notes that stay in the user's Yila account.

Then offer two or three starter requests that fit the user's field, for example:

- "Read the attached paper and draw a 16:9 graphical abstract with Yila."
- "Use Yila to run a deep search on <topic>, including Chinese papers."
- "Check every reference in this draft with Yila and format them in GB/T 7714."

Do not start a paid action (a figure, an edit, a deep search, full-text reading) during onboarding unless the user asked for it. Mention that paid actions use Yila credits and that each result reports what was charged.
