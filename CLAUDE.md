# CLAUDE.md

Claude Code operating notes for this repository. [`AGENTS.md`](AGENTS.md) is the source of
truth for agent behaviour and [`CONTRIBUTING.md`](CONTRIBUTING.md) for inclusion rules; this
file routes to them and adds only what they do not cover. If they disagree, follow them and
fix this file.

## Orientation

- Documentation-only awesome list. The deliverable is `README.md`; there is no application
  code, runtime, or secrets. npm scripts are validation tooling only.
- Typical tasks: add/review entries, triage issues and PRs, fix links, audit taxonomy,
  maintain agent guidance and tooling config.
- The README `## Contents` and `## Taxonomy` table are the live section map and placement
  rubric. Do not rely on a copied section list.

## Where to look

| Task                                         | Read first                                                                                                                                        |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add or edit an entry                         | `CONTRIBUTING.md`, [add-entry skill](.github/skills/add-entry/SKILL.md), target README section and neighbours                                     |
| Vet or review entries (PR/issue)             | [entry-reviewer](.github/agents/entry-reviewer.agent.md), [PR template](.github/PULL_REQUEST_TEMPLATE.md) checklist                               |
| Discover candidates                          | [paper-scout](.github/agents/paper-scout.agent.md)                                                                                                |
| Placement, duplicates, coverage              | [taxonomy-auditor](.github/agents/taxonomy-auditor.agent.md), [coverage-report skill](.github/skills/coverage-report/SKILL.md)                    |
| Failing link or awesome-lint check           | [link-check](.github/skills/link-check/SKILL.md), [awesome-lint](.github/skills/awesome-lint/SKILL.md)                                            |
| Tooling, CI, agent packaging                 | `package.json`, `.prettierignore`, `.markdownlint-cli2.jsonc`, [CI](.github/workflows/ci.yml), `apm.yml`                                          |
| Issue intake                                 | [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/) (suggest-resource, broken-link)                                                              |

The `.github/agents/*.agent.md` files are APM/Copilot-format role briefs, not Claude Code
subagent definitions. Follow them as procedures. For a batch of several independent
candidates, verifying each in a parallel subagent briefed with the relevant agent file is
reasonable; a single entry does not need it.

## Invariants

- Entry format, one unwrapped line: `- [Exact page title](URL) - One neutral sentence. (Year)`.
- Recursion must be central to the resource; window starts **15 May 2022**; prefer the most
  primary source. Details: `CONTRIBUTING.md` (Inclusion Criteria, Time-Window Rule, Source
  Hierarchy, Out-of-Scope).
- **Never fabricate** titles, authors, venues, years, benchmarks, or results. Verify from
  the opened source; search snippets and issue-form metadata are leads, not evidence. If a
  required fact is unverifiable, leave the entry out and say what is missing.
- Search the whole README (title, project, arXiv id, repo name, abbreviation, prose
  cross-references) before adding. Prefer a prose cross-reference to a second listing.
- Minimal diffs. Never reflow `README.md`, `CONTRIBUTING.md`, or `CLAUDE.md` (all
  Prettier-ignored); never run `npm run format` over them.
- When a heading changes, keep Contents, anchors, and cross-references in sync.
- Do not widen linkinator skips, disable lint rules, or remove a resource because of a
  transient 403/429/timeout. Retry and inspect first.
- Keep `package.json`/`package-lock.json` consistent; update `apm.yml` if shipped agent or
  skill paths change. Do not commit ignored root-level `agents/`, `skills/`, `reports/`, etc.

## Validation

Node 22, from the repo root. CI runs all of these, then APM audit and an AgentRC readiness
gate that are not reproducible with npm alone:

```bash
npm ci
npm run build          # Prettier check (not a build)
npm run lint           # markdownlint; excludes README.md and CONTRIBUTING.md
npm run lint:awesome   # awesome-lint on README.md
npm test               # linkinator on README links; skips this repo's own URLs
npm run lint:docs      # remark on the five root docs, including this file
```

Known baseline noise, which should be reported rather than "fixed":

- `lint:docs` exits 0 with many `list-item-indent` warnings (Remark vs Prettier conflict).
  Check only that your change adds no new diagnostics.
- In sandboxed or offline sessions, `lint:awesome` can fail with `Awesome list must reside
  in a valid git repository` (the `awesome-github` rule needs GitHub access), and `npm test`
  can hit network errors. Record these as environment-limited, not as passing.

Automated checks cannot verify relevance, titles, years, or claims. That remains manual.

## Triage dispositions

For PRs and suggestion issues, verify each entry independently of the submitter's claims,
then choose one:

- **Accept**: verified, in scope, correctly formatted and placed, no duplicate, checks pass.
- **Edit as maintainer**: qualifies but has small issues (wording, year, format, section,
  promotional/ranking/time-sensitive phrasing). Fix it directly and note what changed.
- **Request changes**: only the contributor can resolve it (unclear relevance,
  non-authoritative source, claims not matched to the page).
- **Close**: out of scope, unverifiable, duplicate, or outside the window. Link the rule.
- **Park**: borderline recursion-centrality, unclear placement, or needs a new section.
  Do not force it into the README; state exactly what is blocking.

Maintainer comments should be warm, brief, and specific, and should link the relevant
`CONTRIBUTING.md` section. The final decision rests with the human maintainer (`@natnew`,
per CODEOWNERS).

## Done means

- `git diff --check` is clean and the diff has only intended changes, with no encoding or
  line-ending damage and local links that exist with correct case.
- The response or PR includes an evidence note per entry (source URL, verified title/date,
  recursive mechanism, placement, duplicate-search result) and the actual outcome of each
  check, including those skipped or blocked.
- PRs use the PR template; drop its entry checklist when entries are untouched.
