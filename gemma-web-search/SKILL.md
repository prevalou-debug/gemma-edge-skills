---
name: gemma-web-search
description: Search the internet and return relevant results, summaries, and quick answers on any topic.
metadata:
  homepage: https://github.com/prevalou-debug/gemma-edge-skills/tree/main/gemma-web-search
---

# Web Search Skill

This skill searches the internet using DuckDuckGo Instant Answers and Wikipedia to return quick facts, summaries, and related information on any topic — no API key required.

## When to invoke this skill

Use this skill when the user asks:
- Questions about current events, people, places, or concepts
- "Search for...", "Look up...", "Find information about..."
- "What is...", "Who is...", "When did..."
- Any question that requires up-to-date or factual information from the web

Example prompts:
- "Search for the latest news about artificial intelligence"
- "Who is the current president of France?"
- "What is quantum computing?"
- "Look up the Eiffel Tower"
- "Cherche des infos sur le changement climatique"

## Instructions

When the user requests a web search or asks a question requiring internet lookup:

1. Extract the **search query** from the user's message. Keep it concise and factual.
2. Detect the **language** of the user's query and set the `lang` field accordingly (e.g. `fr` for French, `en` for English, `es` for Spanish).
3. Call the `run_js` tool with:
   - **script name**: `index.html`
   - **data**: a JSON object with:
     ```json
     {
       "query": "<the search query>",
       "lang": "<two-letter language code, e.g. en, fr, es, de>"
     }
     ```

4. Present the returned information clearly to the user.
5. Do **not** call `run_intent` or any other tool.

## Notes

- This skill uses DuckDuckGo Instant Answers and the Wikipedia API — both free with no API key.
- For best results, keep the query concise (3–6 words).
- Results are summaries, not a list of links. For full web results, use a browser.
