# Godot Room Design Template

An empty-ish, fill-in-the-blanks template for describing your home (real rooms
and dream rooms alike) in enough detail that Claude can build it as a Godot
project. Rough answers everywhere are fine — partial information beats no
information, and anything left blank just gets a sensible default.

## How to use it

1. **Fill in [`HOUSE.md`](HOUSE.md) first.** Floors, footprint, style, and how
   the rooms connect. This is the most valuable file in the whole template.
2. **Open [`ROOM_CATALOG.md`](ROOM_CATALOG.md)** and check off the rooms that
   exist in your home (or that you want built). It lists 78 rooms across five
   categories — everything from *kitchen* to *secret room* — so it should cover
   your house and most other people's too.
3. **Fill in the sheets under [`rooms/`](rooms/)** for the rooms you checked.
   Each sheet has the same fields plus room-specific ideas at the bottom.
   Delete the sheets that don't apply, or leave them — unchecked rooms are
   simply ignored.
4. **Missing a room?** Copy [`ROOM_TEMPLATE.md`](ROOM_TEMPLATE.md), rename it,
   and drop it in the right `rooms/` category folder.
5. **Hand it back to Claude.** Once sheets are filled in, ask Claude to build
   the rooms into the Godot project under [`godot/`](godot/).

## Measuring tips (the low-effort way)

- **Phone first:** the built-in measure app (LiDAR on many phones) or a cheap
  laser measure gets you room dimensions in minutes. A tape measure and
  "roughly 4 by 3 meters" is also completely fine.
- **Photograph each room from its corners** — 4 photos per room capture more
  layout truth than an hour of note-taking. Reference them in the sheet's
  *References* section.
- Ceiling heights are usually uniform per floor — measure once, note it in
  `HOUSE.md`, and only flag rooms that differ (vaulted, sloped attic, etc.).
- Doors are ~0.8–0.9 m wide and ~2 m tall almost everywhere; only note the
  unusual ones.

## Installing Godot

The project targets **Godot 4.5 stable** (verified working:
`4.5.stable.official.876b29033`).

- **Windows (your Dell):** `winget install --id=GodotEngine.GodotEngine -e`
  or download from <https://godotengine.org/download/windows/>
- **Direct download (all platforms):**
  <https://github.com/godotengine/godot/releases/tag/4.5-stable>
- Godot is a single ~50 MB executable — no installer needed if you use the
  direct download; just unzip and run.

The scaffold in [`godot/`](godot/) uses the **Compatibility renderer** so it
runs well on laptop/integrated graphics; switch to Forward+ later if the
machine handles it.

## Inspiration & suggestions

- **Start with three rooms, not thirty.** A connected kitchen → hallway →
  living room you can walk through feels amazing and takes a weekend; a whole
  house at once stalls out. (Pick your three in `HOUSE.md`.)
- **Grey-box first.** The standard game-dev flow: build every room as plain
  boxes with correct dimensions and door openings, walk it, fix what feels
  wrong, *then* decorate. Dimensions are 80% of whether a space "feels right."
- **Lighting is the cheat code.** A room with plain white walls but layered
  lighting (window light + ceiling + a lamp) looks better than a fully
  furnished room with one flat light. Godot 4's environment glow and volumetric
  fog are your friends.
- **Steal furniture, don't model it.** CC0 asset packs (Kenney.nl furniture
  kits, Quaternius, Poly Haven for textures/HDRIs) give you sofas, beds, and
  kitchens for free — describing *what and where* in the sheets matters far
  more than modeling skill.
- **Add one "impossible" room.** The bonus category (secret room, observatory,
  aquarium wall) exists because a dream room next to your real laundry room is
  what makes the project fun. Highly recommended.
- **Day/night toggle** is a cheap, spectacular feature once rooms exist — one
  DirectionalLight3D rotation and the whole house changes mood.
- **Real-world palettes:** if you're unsure on colors, note a photo or a paint
  brand color name ("Sherwin-Williams Sea Salt") in the sheet — that's precise
  enough to reproduce.

## What's in here

```
godot-room-design/
├── README.md          ← you are here
├── HOUSE.md           ← whole-house sheet (fill this first)
├── ROOM_CATALOG.md    ← checklist of all 78 rooms
├── ROOM_TEMPLATE.md   ← blank sheet for rooms not in the catalog
├── rooms/
│   ├── core/          ← living, kitchen, bedrooms, baths… (18)
│   ├── work-utility/  ← office, laundry, garage, storage… (14)
│   ├── lifestyle/     ← theater, gym, library, bar, pool… (21)
│   ├── outdoor/       ← sunroom, deck, greenhouse, patio… (10)
│   └── bonus/         ← secret room, observatory, vault… (15)
└── godot/             ← empty Godot 4.5 project, ready to open
```
