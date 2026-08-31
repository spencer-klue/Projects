# Audit — 2026-08-31

This template was built by a session without File Voyage context. Audited and
reworked in the second-brain session the same day.

## The one big inaccuracy

The original premise was **"describe your physical house, measure the rooms,
and Claude builds that house in Godot."** File Voyage's world is not a house
anyone measures — it is **generated from a computer's file system**. A room
exists only if the data summons it (no music folder → no studio), and its
size, condition, and contents come from file metadata, not a tape measure.
Spencer had already spotted this trap himself: you cannot hand-design rooms
per machine.

So the unit of design here is not *a room* — it is a **room archetype**: a
reusable recipe ("what a studio is like") that the generator instantiates
with data-driven size, wear, and contents.

## What changed

- `README.md` — rewritten around the vocabulary/archetype premise.
- `HOUSE.md` → **`WORLD.md`** — the hub-and-doors world sheet plus the
  generation rules (data → space), replacing the physical-house sheet.
- `ROOM_TEMPLATE.md` — reworked into an **archetype sheet**: added Trigger,
  Scaling, Condition states, and Hydration states; dropped tape-measure
  fields.
- **`MAPPING.md`** — new: file-system categories → candidate archetypes,
  with the v1 set marked (chosen from Spencer's real recovered corpus).

## What was kept

- The 78 sheets under `rooms/` — untouched, as an **idea palette**. Many map
  beautifully (Vault, Attic, Server Closet, Music Room, Library, Secret
  Passage); fill one only after prefixing it with the archetype fields from
  the new `ROOM_TEMPLATE.md`.
- `godot/` scaffold — Godot 4.5, Compatibility renderer. Verified correct
  for the CPU-only Linux box; keep until a machine with a GPU takes over.
- README craft advice (grey-box first, lighting over furniture, CC0 kits,
  three rooms not thirty) — carried into the rewrite; it applies unchanged.
