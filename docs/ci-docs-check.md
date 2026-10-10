# Docs check (CI)

Pull requests run [.github/workflows/docs-check.yml](../.github/workflows/docs-check.yml). The job **`docs-check`** compares the PR’s three-dot diff (`base...head`) and **fails** when any **watched** design or behaviour file changes without a change under `docs/`.

Add the **`no-docs-needed`** label to skip the requirement when a watched change truly needs no documentation update.

## Watched paths

Keep in sync with the header comment in the workflow and `scripts/docs_check_pr.py`:

- `index.html`
- `*.css`, `*.js`, `*.mjs`, `*.ts`, `*.tsx`, `*.jsx` (repository root)
- `scripts/build.*`, `scripts/*build*`
- `vite.config.*`, `wrangler.toml`, `package.json`

Not watched: `docs/**`, level ASCII data-only edits inside maps (the file `index.html` is still watched as a whole), static images such as `og-card.png`, and other content or data files.

## Local run

```bash
BASE_SHA=<base> HEAD_SHA=<head> PR_LABELS="" python3 scripts/docs_check_pr.py
```

Use merge-base SHAs from your branch and its PR base branch.
