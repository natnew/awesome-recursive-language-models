---
name: awesome-lint
description: Run and interpret the awesome-list compliance linter for README.md. Use before opening or reviewing any pull request that touches the README.
---

# Awesome Lint Skill

Validates that `README.md` complies with the
[awesome list guidelines](https://github.com/sindresorhus/awesome) enforced by
[`awesome-lint`](https://github.com/sindresorhus/awesome-lint). CI runs this on every
push and pull request.

## How to run

```bash
npm run lint:awesome   # runs: awesome-lint README.md
```

The script passes `README.md` explicitly — do not run bare `npx awesome-lint` on
Windows, where absolute `C:\` paths are misparsed as URLs and the run fails with
`Invalid GitHub repo URL`.

## Interpreting results

Common failures and their fixes:

- **`awesome-badge`** — the `[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)`
  badge must sit inside the main `#` heading line.
- **`awesome-toc`** — the `## Contents` section must be the first section; each ToC item
  must match its heading in order. `Contributing` and `License` must **not** appear in
  the ToC.
- **`awesome-license`** — a `## License` _section_ in the README is forbidden; the
  license lives in the `LICENSE` file (CC0) with at most a prose mention elsewhere.
- **`double-link`** — the same URL may appear only once in the document (this includes
  badge links and `#anchor` links).
- **`table-pipe-alignment`** — table pipes must be column-aligned. Format the table
  block through Prettier and paste it back (the README itself is Prettier-excluded).
- **`balanced-punctuation`** — usually mojibake (e.g. `â€”` for an em dash) rather than a
  real unmatched quote; fix the encoding artefact.

## By design, not bugs

- The canonical entry format `- [Title](URL) - Description. (Year)` passes the linter —
  do not "fix" entry punctuation.
- `README.md` is excluded from Prettier and from wholesale reformatting; apply only the
  minimal edit each finding needs.

A clean awesome-lint run is necessary but not sufficient — entries must still satisfy
[`CONTRIBUTING.md`](../../../CONTRIBUTING.md); pair this with the
[`link-check`](../link-check/SKILL.md) skill.
