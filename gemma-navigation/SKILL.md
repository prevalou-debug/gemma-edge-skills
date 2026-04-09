---
name: gemma-navigation
description: Provide turn-by-turn navigation directions and an interactive route map between two locations.
metadata:
  homepage: https://github.com/prevalou-debug/gemma-edge-skills/tree/main/gemma-navigation
---

# Navigation Skill

This skill provides turn-by-turn navigation directions and an interactive map between an origin and a destination, powered by OpenStreetMap and OSRM — no API key required.

## When to invoke this skill

Use this skill when the user asks for:
- Directions from one place to another
- How to get from A to B (by car, foot, or bike)
- Route planning or navigation
- Turn-by-turn instructions between two locations

Example prompts:
- "Navigate from Paris to Lyon"
- "How do I walk from the Eiffel Tower to the Louvre?"
- "Bike route from Amsterdam Centraal to Vondelpark"
- "Directions from New York to Boston by car"

## Instructions

When the user requests navigation or directions:

1. Extract the **origin**, **destination**, and optionally the **transport mode** from the user's message.
   - Default mode is `driving` if not specified.
   - Supported modes: `driving`, `walking`, `cycling`

2. Call the `run_js` tool with:
   - **script name**: `index.html`
   - **data**: a JSON object with the following fields:
     ```json
     {
       "origin": "<origin location as a place name or address>",
       "destination": "<destination location as a place name or address>",
       "mode": "<driving|walking|cycling>"
     }
     ```

3. Do **not** call `run_intent` or any other tool. Do not ask the user for coordinates — use place names directly.

4. Present the returned text directions clearly, and let the interactive map webview render automatically.

## Notes

- This skill uses Nominatim (OpenStreetMap) for geocoding and OSRM for routing. No API key is needed.
- For best results, use specific place names (e.g., "Gare de Lyon, Paris" rather than just "train station").
- If the route cannot be found, the skill will return an error message explaining why.
