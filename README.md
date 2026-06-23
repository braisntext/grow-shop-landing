# grow-shop-landing

Static landing page for grow-shop. `index.html` is served verbatim.

## Git hooks

A committed `.githooks/pre-commit` guards against shipping broken pages: it
fails a commit that introduces a **new** local asset reference (`src`/`href`/
`poster`/`content`/`url()` in any `*.html`) pointing at a file that doesn't
exist on disk. External URLs, in-page anchors, `mailto:`/`tel:`, `data:` URIs
and templated values are ignored.

- Pre-existing breakage is baselined in `.githooks/asset-refs-baseline.txt`;
  only new breakage blocks. Re-snapshot debt with
  `.githooks/pre-commit --write-baseline`.
- In agent clones the Hermes managed git-guard runs this hook automatically
  (`core.hooksPath`). For local dev, enable it once with:
  `git config core.hooksPath .githooks`.
