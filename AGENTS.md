# AGENTS.md

Kracked Quest is a single-file browser platformer: game logic, levels (ASCII maps), and doodle art live in `index.html` on a 960×540 canvas. There is no build step, package manager, or backend.

## Docs rule

Design or behaviour changes (CSS, templates, app JS, build scripts, config) must update `docs/` (usually `docs/design.md`) in the same PR. Use the `no-docs-needed` label only for changes that truly need no docs.

Pull requests run the **docs-check** workflow on watched design/behaviour paths. See [docs/ci-docs-check.md](docs/ci-docs-check.md).

## Sources of truth

| Topic | Document |
| --- | --- |
| Visual style, palette, layout | [docs/design.md](docs/design.md) |
| Local run, hosting, deploy | [README.md](README.md) |
| CI watched paths | [docs/ci-docs-check.md](docs/ci-docs-check.md) |

If docs and code disagree, fix the docs to match the code (or update both in the same PR) and say so in the pull request.

## Layout

| Path | Role |
| --- | --- |
| `index.html` | Entire game and inline styles |
| `og-card.png` | Open Graph preview image |
| `docs/` | Design and CI documentation |

Keep the game in one HTML file unless the maintainer asks to split it.

## Commands

```bash
python3 -m http.server 8000   # local preview at http://localhost:8000/
```

Run the docs check locally (after `fetch-depth` history is available):

```bash
BASE_SHA=<base> HEAD_SHA=<head> python3 scripts/docs_check_pr.py
```

## Notes

- Public entry: [https://polah.app/kracked-quest/](https://polah.app/kracked-quest/) (Cloudflare); the game may redirect to `/kracked/` on that host — see `index.html` and README.
- Touch controls must keep working on mobile when changing input UI.
- No environment variables are required for local play or GitHub Pages deploy.
