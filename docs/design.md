<!-- template: website/design.md v1 -->
# Kracked Quest design

Doodle-style 2D platformer drawn entirely in code on a canvas. This document matches the inline styles and
drawing code in `index.html`.

## Palette

| Token | Value | Use |
| --- | --- | --- |
| Sky | `#79c3f2` | Page background (`html`, `body`) |
| Ink | `#1a1a1a` | Outlines, text, button borders |
| Paper | `#ffffff` (88% on touch buttons) | Touch control fills |
| Shadow | `#1a1a1a` offset 3px | Chunky “sticker” button shadow |

Terrain, characters, and collectibles use additional fills defined in the canvas drawing routines (grass
greens, warm dirt, gold stars, red Kelantan shirt on Pipkin). Prefer reusing existing draw helpers rather than
new hex values.

## Typography

- UI font stack: `'Comic Sans MS', 'Chalkboard SE', sans-serif` (title screen, touch labels).
- In-canvas text uses the same family via `ctx.font` where needed.
- Touch **JUMP** label: 18px, slight letter-spacing.

## Components

- **Canvas** — 960×540 logical size; scaled to fit the viewport with crisp pixels (`devicePixelRatio` capped
  at 2).
- **Touch bar** — Bottom overlay with circular ← / → / JUMP buttons; shown only when touch is available.
- **HUD** — Lives, score, and level name drawn on the canvas during play.
- **Entities** — Pipkin (tabby cat, red shirt with gold batik motifs), grumps, bees, spikes, stars, flag; all
  vector doodles, no sprite sheets.

## Layout

- Full-viewport centered stage: `#wrap` flex-centers the canvas.
- Tile grid: 48px (`T` in code); levels are ASCII character maps.
- Mobile: 150px touch strip; game area remains visible above it.
