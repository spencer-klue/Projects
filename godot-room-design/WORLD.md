# World Overview — the hub and its doors

The File Voyage world is one hub with doors. Each door is a **snapshot of a
machine at a moment in time**; walking through it loads that snapshot's map.
Nothing beyond this page is hand-placed — every room past a door is generated
from the snapshot's data using the archetypes in `rooms/` and the rules below.

## The hub

The only hand-designed space in the game. Design it once, here.

- Concept (harbor / lighthouse / the machine as a house / other):
- Mood in one sentence:
- The guide lives here (the character who has read every snapshot and gives
  hints). Form (person / creature / terminal / lantern):

## The doors (current worlds)

| Door label | Source | Feel |
|---|---|---|
| "Feb 2024 — the night before the crash" | `spencer-pc-2024-image.world.json` | frozen in time, dust motes |
| "The Passport archive" | `my-passport.world.json` | warehouse of sealed crates |
| "The Dell today" | Dell re-scan (pending) | lived-in, cluttered, low on air |

Add a row per new snapshot. Doors are cheap; worlds are generated.

## Generation rules (data → space)

The generator reads a world map and applies these. Tune the numbers by
walking the result, not by guessing.

- **Folder → room; subfolder → doorway deeper.** Folder tree = floor plan.
- **Size → room scale.** Log scale, clamped: a 100 GB folder is a hall, not
  a country.
- **File count → clutter density.** Props per room, capped for playability.
- **Age (untouched years) → condition.** Fresh → lived-in → dusty →
  overgrown → ruins.
- **Hydration → reality.** Real bytes → solid room. Cloud placeholder →
  ghost room (translucent, hollow, flickering). Unreadable/reparse → sealed
  vault needing a key/tool.
- **Category → archetype.** The lookup lives in `MAPPING.md`.
- **Flags → points of interest.** Treasure/duplicate/bloat flags from the
  scanner become glints, echoes, and rot the player can spot from a doorway.

## Whole-world style

- Global palette (2–4 colors that repeat everywhere):
- Visual target: stylized low-poly, flat colors, soft lighting, fog
  (The Big Walk / Untitled Goose Game family) — cheap to render, kind to
  beginners, beautiful through lighting.
- Overall vibe in one sentence:

## Build priority

1. The hub with three working doors (grey-box)
2. One generated floor of the Feb 2024 world
3. The first quest: find the music tech vault

## Notes for Claude

-
