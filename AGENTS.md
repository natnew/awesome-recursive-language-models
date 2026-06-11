# AGENTS.md

Guidance for AI coding agents (Copilot, Claude, Cursor, etc.) working in this repository.
This file is the single source of truth for agent behaviour — keep it consistent with
[`CONTRIBUTING.md`](CONTRIBUTING.md), which holds the full human contributor rules.

## What this repository is

`awesome-recursive-language-models` is a **curated, documentation-only "awesome list"**.
The deliverable is [`README.md`](README.md): a high-signal, well-organised set of resources
on recursive language models, recursive inference, recursive reasoning architectures,
self-calling AI systems, and learned simulation engines for society.

There is **no application code and no runtime.** The only executable parts are dev tools
that lint and validate the list.

## Project layout

- `README.md` — the curated list (the product). Organised by a topic taxonomy.
- `CONTRIBUTING.md` — full inclusion criteria, time-window rule, source hierarchy, and
  the entry format. **Read it before editing the list.**
- `SECURITY.md` — how to report unsafe links or vulnerable dependencies.
- `package.json` — dev tooling scripts (formatting, linting, link checking).
- `.github/` — CI workflow, CODEOWNERS, Dependabot, custom agents, and skills.

## Setup, build, and validation commands

```bash
npm ci                 # install dev tooling from the lockfile
npm run build          # prettier --check (formatting gate; excludes the curated docs)
npm run lint           # markdownlint-cli2 over all Markdown
npm run lint:awesome   # awesome-lint: awesome-list compliance for README.md
npm test               # linkinator: verify every link in README.md resolves
```

**Always run `npm run build`, `npm run lint:awesome`, and `npm test` before opening a
PR.** CI runs the same checks.

## How to add or change a resource

Follow the rules in `CONTRIBUTING.md`. In short:

1. **Verify relevance** — recursion must be central to the method, architecture, inference
   process, evaluation design, agent loop, or self-improvement mechanism. Reject generic
   LLM / prompt-engineering / RAG / agent-framework resources.
2. **Verify the source** — prefer primary sources (arXiv, official project page/repo, docs,
   author/lab page). Open the link, confirm it loads, and confirm the title matches.
3. **Respect the time window** — resources from **15 May 2022 onwards**, unless clearly
   marked as historical context.
4. **Avoid duplicates** — search the README for the title, project name, arXiv id, and
   common abbreviation first. Cross-reference in prose rather than duplicating.
5. **Use the entry format** exactly:

   ```markdown
   - [Resource title](URL) - One concise sentence on what it is and why it matters. (Year)
   ```

6. **Place it in the right taxonomy section.** If unsure which section, propose one in the
   PR description rather than guessing.

## The curation pipeline

This repository ships agent assets (declared in [`apm.yml`](apm.yml)) that divide the
curation work:

- [`paper-scout`](.github/agents/paper-scout.agent.md) — discovers candidate resources
  and pre-screens them against the inclusion criteria (read-only).
- [`curate-entry`](.github/agents/curate-entry.agent.md) — vets a candidate and adds it
  to `README.md` in the canonical format.
- [`entry-reviewer`](.github/agents/entry-reviewer.agent.md) — adversarially re-verifies
  every added or edited entry against its source (read-only).
- [`taxonomy-auditor`](.github/agents/taxonomy-auditor.agent.md) — audits placement,
  cross-references, and duplicates across the whole list, and produces the coverage
  report that tells `paper-scout` where to look next.

Supporting skills: [`add-entry`](.github/skills/add-entry/SKILL.md) (order of operations
for one entry), [`coverage-report`](.github/skills/coverage-report/SKILL.md) (thin/stale
section detection), [`awesome-lint`](.github/skills/awesome-lint/SKILL.md) and
[`link-check`](.github/skills/link-check/SKILL.md) (validation).

## Style and review expectations

- Descriptions are accurate, concise, and non-promotional. No vague praise, no invented
  venues/authors/dates/benchmarks.
- Keep diffs minimal and scoped to the entries you are adding or fixing.
- Do **not** reformat or reflow `README.md` / `CONTRIBUTING.md` wholesale — they are
  hand-curated and excluded from the Prettier gate on purpose.
- A smaller set of well-verified resources beats broad coverage with weak relevance.

## What not to do

- Do not commit the root-level `agents/`, `skills/`, `hooks/`, `workflows/`, `plugins/`,
  or `instructions/` folders — they are intentionally gitignored local tooling.
- Do not add secrets; there is no runtime config (`.env.example` documents this).
- Do not add resources with broken links or unverifiable dates/claims.
