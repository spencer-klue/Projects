# File Voyage — Room Vocabulary (Godot)

The design kit for the File Voyage game world. **Nothing here describes a
specific house or a specific computer.** You design *archetypes* — reusable
recipes for kinds of rooms — and the generator builds each player's unique
world from their actual file system using those recipes. A music studio
appears only for machines that have music; but what "a music studio" looks
like was designed once, here, by you.

Read `AUDIT.md` for how this kit changed from its first draft.

## How to use it

1. **`WORLD.md`** — the hub, the doors (one per machine snapshot), and the
   generation rules that turn data into space. Fill this first.
2. **`MAPPING.md`** — which data summons which archetype. The v1 set is
   marked; start there.
3. **For each v1 archetype**, open its sheet under `rooms/` and rework it
   using the fields in **`ROOM_TEMPLATE.md`** (Trigger, Scaling, Condition
   states, Hydration states). The 78 existing sheets are an idea palette —
   great prompts, not finished specs.
4. **Hand sheets back to Claude** to build into the Godot project under
   `godot/`, wired to real world maps from the scanner.

## Craft rules (kept from v1 — they're right)

- **Grey-box first.** Plain boxes with correct doors, walk it, feel it, then
  decorate. Proportion is 80% of whether a space feels right.
- **Lighting is the cheat code.** Flat-colored walls + layered light beats
  furniture + one flat light. Godot 4's glow and volumetric fog carry the
  Big Walk look.
- **Steal props, don't model them.** CC0 kits: Kenney.nl, Quaternius,
  Poly Haven. Low-poly flat-shaded is the point.
- **Three archetypes before thirty.** Studio, Library, Vault — then walk
  your own 2024 machine and let it tell you what's missing.

## Installing Godot

Targets **Godot 4.5 stable**. The `godot/` scaffold uses the Compatibility
renderer — correct for integrated/CPU graphics; revisit Forward+ when the
Dell (NVIDIA) takes over as the dev machine.

- Linux (this machine): installed at `~/.local/bin/godot`
- Windows (the Dell): `winget install --id=GodotEngine.GodotEngine -e`
- Direct: <https://github.com/godotengine/godot/releases/tag/4.5-stable>

## What's in here

```
godot-room-design/
├── README.md          ← you are here
├── AUDIT.md           ← what changed from the first draft, and why
├── WORLD.md           ← hub, doors, generation rules (fill first)
├── MAPPING.md         ← data → archetype lookup, v1 set marked
├── ROOM_TEMPLATE.md   ← blank ARCHETYPE sheet (Trigger/Scaling/Condition/Hydration)
├── rooms/             ← 78 idea-palette sheets in five categories
└── godot/             ← empty Godot 4.5 project, ready to open
```
