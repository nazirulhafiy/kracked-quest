<!-- template: website/README.md v1 -->
# Kracked Quest website

A tiny 2D platformer in a chunky doodle art style — run, jump, stomp grumps, collect stars, reach the flag.
Starring **Pipkin**, a tabby cat in a red Kelantan shirt with gold batik motifs.

**Play:** [https://polah.app/kracked/](https://polah.app/kracked/) (short public URL on POLAH; `/kracked-quest` on
that host redirects here).

## Deploy

This repository is a **static site** with no build step. Deployment is **GitHub Pages** from the `main` branch
(root directory):

| Layer | What happens |
| --- | --- |
| **Origin** | GitHub Pages serves `index.html`, `og-card.png`, and other tracked files at `https://hafiy.my/kracked-quest/` (and the default `*.github.io` project URL). |
| **Public URL** | **Cloudflare** in front of `polah.app` rewrites `/kracked/` to that GitHub Pages origin path (`/kracked-quest/`). Requests to `https://polah.app/kracked-quest/` redirect to `/kracked/`. |
| **This repo** | No Wrangler, Vercel, or deploy workflow here — pushing to `main` updates what Pages serves. |

Set the GitHub repository **Website** field (About → Website) to `https://polah.app/kracked/` in the GitHub
UI (not stored in git).

## Work on it

**Run locally (no build):** from the repository root:

```bash
python3 -m http.server 8000
```

Open [http://localhost:8000/](http://localhost:8000/). Edit `index.html` and refresh.

**Documentation check (same as CI):** see [AGENTS.md](AGENTS.md#commands).

### Controls

| Action | Keys |
| --- | --- |
| Move | Arrow keys / WASD |
| Jump (tap = short hop) | Space / W / Up |
| Start / continue | Enter |
| Restart level | R |
| Mute | M |

Touch controls appear automatically on mobile.

### Levels

1. **Sunny Slopes** — gentle hills, pits and grumps
2. **Cloudtop Climb** — towers, bees and spike beds

Levels are plain ASCII maps at the top of `index.html` — easy to add more.

## Pages

| Page | Address | Copy source |
| --- | --- | --- |
| Game | `index.html` | Inline in `index.html` (title screen, HUD, level names) |
| Social preview | `og-card.png` | Static image referenced from `<meta>` tags |

## Languages

None — English only.

## Content sources

None — no CMS or generated HTML; all player-facing copy is in `index.html`.

## App dependencies

None — no runtime packages. The game runs in the browser from the committed static files.
