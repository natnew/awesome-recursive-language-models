---
name: link-check
description: Validate that every link in the curated list resolves and points at the intended resource. Use before opening or reviewing a pull request that adds or edits entries.
---

# Link Check Skill

Verifies the integrity of links in `README.md` for the
**awesome-recursive-language-models** list.

## When to use

- Before opening a PR that adds or edits resource entries.
- When reviewing a PR, to confirm new links are live.
- Periodically, to catch link rot in the existing list.

## How to run

```bash
npm test          # runs: linkinator README.md --markdown
```

`linkinator` parses the Markdown, extracts every link, and reports any that are broken,
redirected, or unreachable.

Self-referential links (this repository's own GitHub URLs) are skipped via `--skip`:
while the repository is private they return 404 to anonymous checkers even though they
are correct. Remove the skip once the repository is public if you want them re-checked.

## Interpreting results

- **OK** — link resolves (200). No action.
- **BROKEN (404/410/timeout)** — fix or remove the entry. If the resource genuinely moved,
  update the URL to the new primary source.
- **Redirect (3xx)** — prefer updating the entry to the final canonical URL.

## Beyond reachability

A live link is necessary but not sufficient. Per [`CONTRIBUTING.md`](../../../CONTRIBUTING.md),
also confirm the page title matches the entry and the source is primary (not a secondary
summary), and that the resource still satisfies the recursion-centric inclusion criteria.
