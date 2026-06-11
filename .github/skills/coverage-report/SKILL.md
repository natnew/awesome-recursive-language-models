---
name: coverage-report
description: Measure how comprehensive and current the list is — entries per section and per year, with thin and stale sections flagged. Use before planning content expansion or periodically as a health check.
---

# Coverage Report Skill

Computes coverage statistics for `README.md` in the
**awesome-recursive-language-models** list, so growth effort goes where the list is
weakest.

## When to use

- Before a content-expansion pass, to pick target sections.
- Periodically, to check the list is keeping pace with the field.
- After a large PR, to see how coverage shifted.

## How to compute

Every entry is one line matching `- [Title](URL) - Description. (Year)`. For each
taxonomy section of `README.md`:

1. Count the entry lines.
2. Extract each trailing `(Year)` and record the newest year.
3. Note prose cross-references ("See the core papers above…") — they mitigate a low
   count but do not replace entries.

Example one-liner for the raw counts (run from the repo root):

```bash
awk '/^## /{section=$0} /^- \[/{count[section]++} END{for (s in count) print count[s], s}' README.md | sort -rn
```

## Interpreting results

- **Thin** — fewer than 5 entries: a target for the
  [`paper-scout`](../../agents/paper-scout.agent.md) agent.
- **Stale** — newest entry older than ~12 months: the field has likely moved; sweep for
  recent work.
- **Uncovered pattern** — a row of the Taxonomy table with no example entries anywhere:
  highest-priority gap.

A section being thin is not by itself a problem — per
[`CONTRIBUTING.md`](../../../CONTRIBUTING.md), a smaller set of well-verified resources
beats broad coverage with weak relevance. Use the report to direct _search_ effort, not
to justify padding.

## Output

A markdown table — `section | entries | newest year | status (ok / thin / stale)` —
followed by a short list of recommended targets for the next expansion pass.
