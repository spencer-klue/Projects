# Mapping — file system → room archetype

The generator's lookup table. Left column is what the scanner knows about a
folder; right column is the archetype it summons. **v1** rows are the launch
set — chosen because they all actually occur in Spencer's recovered corpus,
so the first generated world exercises every one of them.

| Data signal | Archetype (sheet in `rooms/`) | v1 |
|---|---|---|
| Music production (DAW projects, samples, plugins) | Recording Studio (`lifestyle/recording-podcast-studio.md`) | ✅ |
| Documents / coursework / PDFs | Library (`lifestyle/library-reading-room.md`) | ✅ |
| Downloads | Warehouse (`work-utility/storage-room.md`) | ✅ |
| Old Downloads (1 yr+ untouched) | Attic (`work-utility/attic.md`) | ✅ |
| AppData / system / caches | Server Closet (`work-utility/server-network-closet.md`) | ✅ |
| Pictures / camera rolls | Gallery (no sheet yet — copy ROOM_TEMPLATE.md) | ✅ |
| Cloud placeholder dirs (0 real bytes) | Ghost Room (state, applies to any archetype) | ✅ |
| Unreadable / reparse / locked | Vault (`bonus/vault.md`) | ✅ |
| Hidden files & dirs | Secret Passage (`bonus/secret-room-hidden-passage.md`) | ✅ |
| The hub | designed by hand in `WORLD.md` | ✅ |
| Code / dev projects (git, IDE workspaces) | Workshop (`work-utility/workshop.md`) | |
| Videos / media | Home Theater (`lifestyle/home-theater-media-room.md`) | |
| Games / installers | Arcade (`bonus/arcade-room.md`) | |
| Duplicate suspects | Hall of Mirrors (copy ROOM_TEMPLATE.md) | |
| Virtual machines / disk images | Basement stairs down to a nested world | |
| Email archives | Post Office (copy ROOM_TEMPLATE.md) | |
| Financial / identity documents | Safe Room (`bonus/panic-safe-room.md`) | |

Unmatched folders fall back to a plain **Hallway/Storage** so generation never
fails. Every sheet you fill must use the archetype fields (Trigger, Scaling,
Condition, Hydration) from `ROOM_TEMPLATE.md` — the original 78 sheets are an
idea palette, not finished specs.

## The first quest, mapped

"Find the South Africa music class" plays as: hub → Feb 2024 door → Library
district (Documents) → the OneDrive wing where rooms turn ghostly
(placeholders) → one **sealed Vault** among the ghosts → open it with the
raw-disk key → inside, a Recording Studio, intact, with the class on the
shelves. Every beat of that quest is literally true — it is this session's
recovery, replayed.
