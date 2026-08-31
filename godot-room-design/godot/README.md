# Room Design — Godot project

An intentionally empty Godot 4.5 project (Compatibility renderer, laptop
friendly). Open it in Godot via **Import** → select this folder's
`project.godot`.

Layout convention for when rooms get built:

- `scenes/rooms/` — one scene per room (`living_room.tscn`, …)
- `scenes/house/` — the assembled house (floors, room instances, doors)
- `assets/` — imported models, textures, and materials
- `scripts/` — GDScript (player controller, door logic, day/night, …)

Rooms are built from the filled-in sheets in `../rooms/` — see the top-level
[`README.md`](../README.md) for the workflow.
