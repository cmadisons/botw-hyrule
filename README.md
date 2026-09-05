# BOTW — Hyrule

Breath of the Wild reference data and browser toys.

## Contents

| File | What it is |
|---|---|
| [`BOTW-Shrine-Guide.md`](BOTW-Shrine-Guide.md) | All 136 shrines (120 base + 16 *Champions' Ballad*) with Sheikah Slate coordinates and step-by-step walkthroughs |
| [`hyrule-shrine-atlas.html`](hyrule-shrine-atlas.html) | Searchable shrine atlas — filter by region, track completion |
| [`great-plateau.html`](great-plateau.html) | A playable Hyrule in the browser. Three.js, single file, no build step |
| [`reference/`](reference/) | Map screenshots |

## Coordinates

Given in Sheikah Slate order — **(X, Y, Z)**, where X is east(+)/west(−),
Y is north(+)/south(−), and Z is elevation above sea level.

## great-plateau.html

The terrain is not random. The Great Plateau is 100 hand-authored sculpting
passes over a 1.6 km grid; a second, coarser 10 km heightmap carries all
fifteen regions of Hyrule around it, so the Plateau's cliffs fall into real
Hyrule Field rather than the void.

Open the file in a browser — that's the whole install.

### Loading a real heightmap

Press **N** in game to open the terrain loader, then drop in a heightmap
extracted from your own copy of the game. Hyrule is rebuilt from it; the
Great Plateau's fine sculpt stays stamped on top.

It takes either a headerless `.r16` / `.raw` / `.hght` of uint16
little-endian samples (side length inferred as `sqrt(bytes/2)`), or a `.png` —
8-bit grey, or 16 bits packed into the red and green channels, detected
automatically. Anything larger than 2048 square is box-averaged down, since
the world grid only samples 401 points across.

Register the raster with the span/offset/rotation fields — every region is
pinned on the preview, so you can see when it lines up. **Auto-fit** maps the
raster's own range onto Hyrule; **TSCB** uses the documented full-scale
mapping instead (uint16 across a max terrain height of 800). The blend slider
crossfades between the real data and the sculpt, and **Clear** restores the
sculpt exactly.

Nothing is shipped here — extract your own from `content/Terrain/A/MainField`
with [botw-tools](https://github.com/MrCheeze/botw-tools) or
[BotWHeightMapConverter](https://github.com/AndrewKBorland/BotWHeightMapConverter).

## Note

Contains no Nintendo assets. Coordinates and shrine names are reference data;
the terrain, models and audio are original.
