# Gemma Navigation Skill

A navigation skill for [Google AI Edge Gallery](https://github.com/google-ai-edge/gallery) powered by Gemma 4 E2B. Provides turn-by-turn directions and an interactive route map — entirely on-device reasoning, no API key required.

## What it does

- Accepts a natural language navigation request (origin, destination, and optional transport mode)
- Geocodes locations using [Nominatim](https://nominatim.openstreetmap.org/) (OpenStreetMap)
- Computes the route via [OSRM](https://project-osrm.org/) (Open Source Routing Machine)
- Returns turn-by-turn text directions in the chat
- Displays an interactive [Leaflet.js](https://leafletjs.com/) map with the route drawn

## Supported transport modes

| Mode | Keyword |
|------|---------|
| Car (default) | `driving` |
| On foot | `walking` |
| Bicycle | `cycling` |

## Example prompts

```
Navigate from Paris to Lyon
How do I walk from the Eiffel Tower to the Louvre?
Bike route from Amsterdam Centraal to Vondelpark
Directions from New York to Boston by car
```

## File structure

```
gemma-navigation/
├── SKILL.md                 # Skill definition (required by Edge Gallery)
├── README.md                # This file
├── scripts/
│   └── index.html           # JS execution engine (geocoding + OSRM routing)
└── assets/
    └── map.html             # Interactive Leaflet.js map webview
```

## Installing in Edge Gallery

### Via URL (recommended)

The skill is hosted on GitHub Pages. In Edge Gallery → Agent Skills → Add skill by URL:

```
https://prevalou-debug.github.io/gemma-edge-skills/gemma-navigation/
```

> **Note**: GitHub Pages must be enabled on the repository (`main` branch, root folder) for the URL above to work. Make sure `.nojekyll` exists at the repo root (already included).

### Via local file (Android)

```bash
adb push gemma-navigation/ /sdcard/Download/gemma-navigation/
```

Then import from the device's Download folder in Edge Gallery.

## Technical details

- **Geocoding**: Nominatim OpenStreetMap API — free, no key needed
- **Routing**: OSRM public demo server — free, no key needed (rate limits may apply for heavy use)
- **Map rendering**: Leaflet.js 1.9.4 via CDN — open source
- **Gemma model**: Optimised for Gemma 4 E2B (Edge 2B parameters)

## License

Copyright 2026 Google LLC. Licensed under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).
