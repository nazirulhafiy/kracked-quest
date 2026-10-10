<!-- template: AGENTS.md v1 -->
# AGENTS.md

## What it is

Kracked Quest is a single-file browser platformer: all game logic and doodle art live in `index.html` on a
960×540 canvas. There is no build step, package manager, or backend. It ships as static files on GitHub Pages
and is served on the public web through the POLAH proxy at `https://polah.app/kracked/`.

## Sources of truth

| Question | Document |
| --- | --- |
| Visual style, palette, layout | [docs/design.md](docs/design.md) |
| How to run and deploy | [README.md](README.md) |

**Docs rule:** Read this file, then the document the task touches (especially [docs/design.md](docs/design.md)).
If the docs and the code disagree, fix the docs first and say so in the pull request.

Organization handbook:
https://github.com/yangflow-repopro/.github/tree/main/handbook — rules for AI collaborators:
https://github.com/yangflow-repopro/.github/blob/main/handbook/core/agents.md

## Directory boundaries

| Path | Role |
| --- | --- |
| `index.html` | Entire game: levels (ASCII maps), rendering, input, audio |
| `og-card.png` | Open Graph / social preview image |
| `docs/` | Design and other context docs |
| `.github/workflows/` | CI (documentation compliance) |

Do not split the game across modules unless the maintainer asks; the point of this repository is one file to
open and play.

## Commands

| Command | Purpose |
| --- | --- |
| `python3 -m http.server 8000` | Local preview at `http://localhost:8000/` (no build) |
| `python3 .org/scripts/check-docs.py .` | Same documentation check CI runs (after checking out the org handbook to `.org`) |

CI on pull requests and `main` runs the reusable **Docs check** workflow (`.github/workflows/docs.yml`).

## Project rules

- Keep the game playable with no build step and no production dependencies.
- Level data stays as ASCII maps at the top of `index.html` unless the maintainer moves them.
- Touch controls must keep working on mobile; test narrow viewports when changing input UI.
- Canonical public URL is `https://polah.app/kracked/`; legacy hosts redirect via the script in `index.html`.
- When changing colors, typography, or HUD chrome, update [docs/design.md](docs/design.md) in the same pull
  request.

## Red lines

Credentials never appear in pull requests, issues, logs, reports, or chat. Signing, release, and anything sent
to an external service need the maintainer's confirmation. No blind staging (`git add -A`). See
https://github.com/yangflow-repopro/.github/blob/main/handbook/core/agents.md
