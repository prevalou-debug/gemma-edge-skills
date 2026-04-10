# Gemma Web Search Skill

A web search skill for [Google AI Edge Gallery](https://github.com/google-ai-edge/gallery) powered by Gemma 4 E2B. Searches the internet using **DuckDuckGo Instant Answers** and **Wikipedia** — no API key required.

## What it does

- Takes a natural language search query from the user
- Fetches instant answers from DuckDuckGo (definitions, quick facts, calculations)
- Fetches a summary from Wikipedia in the user's language
- Returns a formatted text summary in the chat
- Opens a DuckDuckGo search results page as an interactive webview

## Example prompts

```
Search for artificial intelligence
Who is Elon Musk?
What is quantum computing?
Cherche des infos sur le Mont Blanc
¿Qué es el cambio climático?
```

## File structure

```
gemma-web-search/
├── SKILL.md          # Skill definition (required by Edge Gallery)
├── README.md         # This file
└── scripts/
    └── index.html    # JS engine: DuckDuckGo + Wikipedia APIs
```

## Installing in Edge Gallery

In Edge Gallery → Agent Skills → Add skill by URL:

```
https://prevalou-debug.github.io/gemma-edge-skills/gemma-web-search/
```

> GitHub Pages must be enabled on the repository for this URL to work.

## Technical details

| Source | API | Key required |
|--------|-----|-------------|
| DuckDuckGo Instant Answers | `https://api.duckduckgo.com` | No |
| Wikipedia | `https://{lang}.wikipedia.org/w/api.php` | No |
| Search results page | DuckDuckGo webview | No |

Both APIs have open CORS headers, compatible with Edge Gallery's WebView.

## License

Copyright 2026 Google LLC. Licensed under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).
