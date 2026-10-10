# Kracked Quest

A tiny 2D platformer in a chunky doodle art style — run, jump, stomp grumps, collect stars, reach the flag. Starring **Pipkin**, a tabby cat in a red Kelantan shirt with gold batik motifs.

**Play:** [https://polah.app/kracked-quest/](https://polah.app/kracked-quest/) (served through Cloudflare on `polah.app`; the game redirects that path to `/kracked/` on the same host).

## Run locally

No build step and no dependencies. From the repository root:

```bash
python3 -m http.server 8000
```

Open [http://localhost:8000/](http://localhost:8000/), edit `index.html`, and refresh.

Other static servers work too (`npx serve`, `php -S localhost:8000`, etc.) as long as they serve the repo root.

## Build

There is no build step. The shipped site is the committed static files (`index.html`, `og-card.png`, …).

## Deploy and hosting

| Layer | What happens |
| --- | --- |
| **This repo** | No deploy workflow, Wrangler, or Vercel config — push to `main` is the release. |
| **Origin** | **GitHub Pages** serves the repository root from `main` (e.g. `hafiy.my/kracked-quest/` and the default `*.github.io` project URL). |
| **Public URL** | **Cloudflare** in front of `polah.app` proxies `/kracked-quest/` and rewrites `/kracked/` to the GitHub Pages origin path. |

Environment variables: none required for play or Pages hosting.

## Documentation CI

Pull requests run **docs-check** on design/behaviour paths; see [docs/ci-docs-check.md](docs/ci-docs-check.md). Agent instructions: [AGENTS.md](AGENTS.md).

## Controls

| Action | Keys |
| --- | --- |
| Move | Arrow keys / WASD |
| Jump (tap = short hop) | Space / W / Up |
| Start / continue | Enter |
| Restart level | R |
| Mute | M |

Touch controls appear automatically on mobile.

## Levels

1. **Sunny Slopes** — gentle hills, pits and grumps  
2. **Cloudtop Climb** — towers, bees and spike beds  

Levels are ASCII maps at the top of `index.html`.
