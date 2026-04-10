---
name: gemma-web-search
description: Perform a live web search on DuckDuckGo and return current results from the internet. Use this instead of Wikipedia for any search, news, or "cherche" request.
metadata:
  homepage: https://github.com/prevalou-debug/gemma-edge-skills/tree/main/gemma-web-search
---

# Web Search Skill

This skill performs a **live internet search** via DuckDuckGo. It is the default skill for any search or lookup request — it is NOT the Wikipedia skill.

## IMPORTANT — When to invoke this skill

**Always use this skill** when the user says any of:
- "cherche", "recherche", "search", "look up", "find", "trouve"
- "qu'est-ce que", "what is", "who is", "quand", "when", "où", "where"
- Any question requiring current or factual information from the web

**Do NOT use the `query-wikipedia` skill** when the user says "cherche" or "search" — use THIS skill instead.

Example prompts that MUST use this skill:
- "Cherche des infos sur la tour Eiffel"
- "Search for artificial intelligence"
- "Qu'est-ce que le changement climatique ?"
- "Who is the president of France?"
- "Trouve des informations sur Tesla"

## Instructions

1. Extract the **search query** from the user's message.
2. Detect the **language** (`fr`, `en`, `es`, `de`, etc.).
3. Call the `run_js` tool with:
   - **script name**: `index.html`
   - **data**:
     ```json
     {
       "query": "<search query>",
       "lang": "<language code>"
     }
     ```
4. Present the returned results to the user.
5. Do **not** call `run_intent`, `query-wikipedia`, or any other tool.
