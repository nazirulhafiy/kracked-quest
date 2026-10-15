# Kracked Quest design

Doodle-style 2D platformer drawn in code on a canvas. Values below match `index.html`.

## Palette

| Token | Value | Use |
| --- | --- | --- |
| Sky | `#79c3f2` | Page background (`html`, `body`) |
| Ink | `#1a1a1a` | Outlines, text, button borders |
| Paper | `#ffffff` (88% on touch buttons) | Touch control fills |
| Shadow | `#1a1a1a` offset 3px | Chunky button shadow |

Terrain, characters, and collectibles use additional fills in the canvas drawing routines (grass greens, dirt, gold stars, Pipkin’s red Kelantan shirt with gold batik). Reuse existing draw helpers before adding new colours.

## Typography

- UI: `'Comic Sans MS', 'Chalkboard SE', sans-serif` (title screen, touch labels).
- In-canvas text uses the same family via `ctx.font`.
- Touch **JUMP** label: 18px with slight letter-spacing.

## Components

- **Canvas** — 960×540 logical size; scaled to the viewport with crisp pixels (`devicePixelRatio` capped at 2).
- **Touch bar** — Bottom overlay with circular ← / → / JUMP; shown when touch is available.
- **HUD** — Lives, score, and level name on the canvas during play.
- **Entities** — Pipkin, grumps, bees, spikes, stars, flag; vector doodles, no sprite sheets.

## Layout and behaviour

- `#wrap` flex-centers the canvas in the viewport.
- Tile grid: 48px (`T` in code); levels are ASCII character maps at the top of `index.html`.
- Mobile: ~150px touch strip; play area stays above it.
- Legacy host paths redirect to `https://polah.app/kracked/` via an inline script in `index.html`.

## Analytics

- Google Analytics 4: measurement ID `G-B3BZXWWDH9` (the shared polah.app property), tag in `<head>` of `index.html`. Served at polah.app/kracked-quest/.
- Cloudflare Web Analytics: polah.app is proxied by Cloudflare with Web Analytics auto-install enabled, so the beacon is injected at the edge; no snippet in code.
- No Content-Security-Policy is set; if one is added, allow `www.googletagmanager.com` and `*.google-analytics.com`.
