---
name: gemma-web-search
description: Search the web using DuckDuckGo and return current results for any topic or question.
metadata:
  homepage: https://github.com/prevalou-debug/gemma-edge-skills/tree/main/gemma-web-search
---

# Web Search Skill

This skill searches the internet via DuckDuckGo and returns results for any topic, question, or current event.

## When to invoke this skill

Use this skill when the user asks:
- "Cherche...", "Recherche...", "Search for...", "Find..."
- "Qu'est-ce que...", "What is...", "Who is...", "Where is..."
- Any question requiring current or factual information from the web

Example prompts:
- "Cherche sur le nouveau modele Meta"
- "Search for artificial intelligence news"
- "Qu'est-ce que le changement climatique ?"

## Instructions

When the user wants a web search:

1. Extract the **search query** from the user's message.
2. Detect the **language** of the message (`fr`, `en`, `es`, `de`, etc.).
3. Call the `run_js` tool with:
   - **script name**: `gemma-web-search.html`
   - **data**: `{ "query": "<search query>", "lang": "<language code>" }`

Do not call any other tool.
