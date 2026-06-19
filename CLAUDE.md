# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A curated, **documentation-only "awesome list"**. The deliverable is `README.md`: a
high-signal set of resources on recursive language models, recursive inference, recursive
reasoning architectures, self-calling AI systems, and learned simulation engines for
society. There is **no application code and no runtime** — the only executables are dev
tools that lint and validate the list. `AGENTS.md` and `CONTRIBUTING.md` are the source of
truth for curation rules; keep this file consistent with them.

Your job here is maintainer support: README upkeep, PR review, issue triage, link/quality
checks, section placement, duplicate detection, and short, friendly maintainer comments.

Work **alongside** the repository's agent-assisted curation pipeline (`paper-scout`,
`curate-entry`, `entry-reviewer`, `taxonomy-auditor` — see `README.md`), not as an
uncontrolled autonomous updater: review entries like `entry-reviewer`, format and place
them like `curate-entry`, check section health and duplicates like `taxonomy-auditor`, and
keep final decisions aligned with maintainer judgement.

## Validation commands

Run these before approving or committing any change to `README.md`:

```bash
npm ci                 # install dev tooling from the lockfile
npm run build          # prettier --check (formatting gate; curated docs are excluded)
npm run lint           # markdownlint-cli2 over all Markdown
npm run lint:awesome   # awesome-lint compliance for README.md
npm test               # linkinator: verify every README.md link resolves
```

`npm run format` rewrites with Prettier — do **not** run it against `README.md` /
`CONTRIBUTING.md` (they are hand-curated and excluded by `.prettierignore`). CI runs the
same gates plus APM and AgentRC readiness steps.

## What belongs / what does not

Belongs — recursion must be **central** to the method, architecture, inference process,
evaluation design, agent loop, or self-improvement mechanism:
- self-recursive inference, tree/graph recursion, iterative refinement, recursive
  architectures, recursive retrieval, recursive self-improvement, simulation recursion.

Does **not** belong:
- generic LLM or prompt-engineering resources;
- RAG where recursive retrieval/summarisation/decomposition is not central;
- broad agent lists/frameworks without recursive planning, reflection, self-correction, or
  tool-use loops;
- unverified blogs, newsletters, social-media summaries;
- broken links, or anything whose date/claims can't be matched to the source.

## Awesome-list quality standards

- A smaller set of well-verified resources beats broad coverage with weak relevance.
- **Time window:** resources from **15 May 2022 onwards**, unless clearly marked as
  historical context.
- **Source hierarchy** (prefer the most authoritative): arXiv / conference page → official
  project page → official GitHub repo → official docs → author/lab page → high-quality
  secondary explanation only when it adds clear value. Prefer official sources, papers,
  repos, datasets, docs, and durable project pages over thin wrapper pages.

## README formatting rules

- Entry format, exactly: `- [Title](URL) - One concise sentence. (Year)`
  - Single hyphen separator with surrounding spaces; sentence ends with a period; year in
    parentheses at the very end.
- Title matches the linked page exactly. Year is verified from the page itself.
- Sections within a topic are bullet lists; cross-references to other sections are short
  prose lines (e.g. "See Tree of Thoughts in the core papers…"), not duplicate entries.
- Keep diffs minimal and scoped to the entries touched. Never reflow or reformat the whole
  README.

## Link quality rules

- Open the link; confirm it loads and the on-page title matches the entry title.
- Confirm it's the intended primary resource, not a secondary summary (unless no primary
  source exists, in which case list the primary too).
- The linkinator test skips internal `github.com/natnew/...` links by design; still
  sanity-check those manually.

## Neutral description style

State what the resource is and why it matters for recursion. Avoid vague praise,
exaggerated importance, and unsupported claims. Remove or neutralise **promotional,
time-sensitive, ranking, pricing, or unsupported** language. Never invent venues, authors,
dates, benchmarks, or results, and don't copy abstracts without checking relevance.

**Do not fabricate.** Never add or modify a paper, repo, benchmark, author, year, venue,
result, claim, or implementation detail unless it can be verified from the linked source or
another authoritative project source. If a detail can't be verified, leave it out and flag
it rather than guessing.

## Section placement

Current taxonomy sections (see the README `## Contents`): Core Papers · Recursive Language
Models · Recursive Reasoning Architectures · Inference-Time Recursion · Recursive Agents
and Tool Environments · Recursive Evaluation and Verification · Recursive Planning and
Search · RL and Self-Improving Systems · Simulation Recursion and Social Simulation ·
Benchmarks and Evaluation Tasks · Open-Source Implementations.

- Place by the dominant recursive mechanism. Papers → topical section or Core Papers;
  code → Open-Source Implementations; datasets/tasks → Benchmarks and Evaluation Tasks.
- If placement is genuinely unclear, propose a section in the PR/issue rather than guessing.

**When unsure, don't force it.** If recursion-centrality, source authority, section
placement, or eligibility is genuinely borderline, do not push the entry into the README.
Park the issue/PR, leave a brief maintainer note explaining exactly what's uncertain, and
ask for maintainer review instead of guessing. Keep the note friendly and low-friction.

## Duplicate checking

Before accepting an entry, search the README for the **title, project name, arXiv id, repo
name, and common abbreviation**. Don't list the same work in multiple sections without a
strong reason — prefer a prose cross-reference.

## PR triage workflow

1. Read the PR description and the entry checklist in `PULL_REQUEST_TEMPLATE.md`.
2. Verify each entry: relevance (recursion central), source authority, title/year match,
   time window, format, placement, no duplicate.
3. Confirm the diff is minimal and the README wasn't reflowed.
4. Confirm `npm run lint`, `npm run lint:awesome`, and `npm test` pass (or run them).
5. Decide using the disposition guide below.

## Issue-to-entry workflow

Suggestions arrive via the "Suggest a resource" issue form (URL, title, year, proposed
section, recursion-centrality rationale). To convert one:
1. Re-verify the link, title, year, and recursion centrality independently of the form.
2. Check the time window and search for duplicates.
3. Draft the entry in canonical format and place it in the proposed/most-fitting section.
4. Validate, then open the PR (or apply directly if it's a small safe fix — see below).

## Disposition guide

- **Accept as-is** — entry is relevant, verified, correctly formatted and placed, no
  duplicate, checks pass.
- **Edit as maintainer** — the resource qualifies but has small fixable issues (wording,
  year, formatting, section, neutralising promo language). Make the fix directly rather
  than asking the contributor for trivial edits; note what you changed.
- **Request changes** — substantive problems only a contributor can resolve: relevance is
  unclear, source isn't authoritative, claims can't be matched to the page.
- **Close** — out of scope, unverifiable, duplicate, or outside the time window with no
  historical-context justification. Explain briefly and kindly; link the relevant rule.
- **Park** — promising but needs discussion (e.g. a new section, borderline relevance).
  Label/leave open with a clear note on what's blocking.

## Maintainer authority

Small, safe fixes may be made **directly** by the maintainer — typos, year corrections,
formatting, section moves, trimming promotional/time-sensitive/ranking/pricing/unsupported
phrasing — instead of round-tripping with the contributor for unnecessary edits. Always
neutralise such phrasing before an entry lands. Reserve change requests for issues that
genuinely need the contributor.

## Contributor communication style

Warm, concise, respectful, low-friction. Thank contributors, be specific about what's
needed and why, link the exact rule in `CONTRIBUTING.md`. Prefer fixing it yourself over asking.


