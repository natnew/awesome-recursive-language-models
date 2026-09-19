# AGENTS.md

Practical guidance for agents maintaining this repository. This file is the source of
truth for repository-specific agent behaviour; [`CONTRIBUTING.md`](CONTRIBUTING.md)
defines resource eligibility and contributor rules. Keep [`CLAUDE.md`](CLAUDE.md) and
the agent assets consistent with both. Do not silently change inclusion policy while
adding entries or fixing tooling.

## What this repository is

`awesome-recursive-language-models` is a **curated, documentation-only "awesome list"**.
The deliverable is [`README.md`](README.md): a high-signal, well-organised set of resources
on recursive language models, recursive inference, recursive reasoning architectures,
self-calling AI systems, and learned simulation engines for society.

There is **no application code, runtime, deployment, or required secret configuration**.
The executable parts are development tools that validate the list and agent assets.
Success means accurate, useful curation with a small, reviewable diff — not more entries
or a higher readiness score at the expense of quality.

## Start here

1. Run `git status --short` and inspect the relevant diff. Preserve existing user changes.
2. Read `CONTRIBUTING.md` before changing entries, and the target README section plus
   its neighbours before choosing placement. Use the live Contents and Taxonomy as the map.
3. Read the matching agent or skill below for curation tasks. For tooling changes, inspect
   [`package.json`](package.json), the relevant configuration, and
   [CI](.github/workflows/ci.yml) rather than assuming the scripts' behaviour.
4. Make the smallest change that satisfies the request, validate it, and report the result.

Useful reference files:

- [PR template](.github/PULL_REQUEST_TEMPLATE.md) — entry and validation checklists.
- [Issue templates](.github/ISSUE_TEMPLATE/) — resource suggestions and broken-link reports.
- [`apm.yml`](apm.yml) — shipped agent, skill, and MCP asset declarations.
- [`SECURITY.md`](SECURITY.md) — reporting unsafe links or vulnerable dependencies.
- [`.env.example`](.env.example) — documents that this repository needs no runtime secrets.

## Setup, build, and validation commands

Run from the repository root. CI uses **Node.js 22** and npm with the committed
`package-lock.json`. Use `npm ci` for a fresh checkout or changed lockfile; reuse an
up-to-date installation otherwise.

```bash
npm ci
npm run build
npm run lint
npm run lint:awesome
npm test
npm run lint:docs
```

Run all five checks before opening a PR, including for guidance-only changes.

| Command                | What it checks and its limits                                                                                                                                     |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `npm run build`        | Prettier formatting, not an application build. Excludes `README.md`, `CONTRIBUTING.md`, `CLAUDE.md`, and generated/vendor files via `.prettierignore`.            |
| `npm run lint`         | Markdown style with `.markdownlint-cli2.jsonc` and `.markdownlint.json`. Respects gitignore; excludes `README.md` and `CONTRIBUTING.md`.                          |
| `npm run lint:awesome` | Awesome-list compliance for `README.md`. Keep the explicit filename in the script; bare awesome-lint can misinterpret Windows paths.                              |
| `npm test`             | Live README link reachability. Skips URLs matching `github.com/natnew/awesome-recursive-language-models`; manually verify changed self-links and section anchors. |
| `npm run lint:docs`    | Remark checks on `README.md`, `AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md`, and `SECURITY.md`. Inspect diagnostics as well as the exit code.                       |

CI additionally installs and audits APM assets and runs an AgentRC readiness gate. When
changing agent packaging or readiness configuration, check those steps in the workflow
too. Passing the npm checks alone does not establish that the full CI job passes.

For failures, distinguish problems introduced by the diff from existing findings and
environment restrictions. Record the failing command and relevant diagnostics. A timeout,
HTTP 403/429, or network restriction is not proof that a resource disappeared: inspect
the source and retry the affected link before proposing removal. Do not widen link skips,
disable lint rules, or rewrite unrelated content just to make a check green. Automated
checks cannot establish relevance, title/year accuracy, or support for a description.

On Windows, a CRLF checkout can make Prettier flag otherwise unchanged files because
it expects LF. Compare against the committed content before treating this as formatting
drift. The current Remark preset also reports `list-item-indent` warnings for lists
formatted by Prettier; report that mismatch rather than repeatedly reformatting between
the two tools or suppressing the rule.

## How to add or change a resource

Follow `CONTRIBUTING.md` and the [add-entry procedure](.github/skills/add-entry/SKILL.md).

1. **Search for duplicates first.** Search the whole README for the title, project name,
   arXiv identifier, repository name, and common abbreviation, including prose references.
   Different URLs or paper revisions can refer to the same work. Prefer a prose
   cross-reference to a second listing; explain any justified exception.
2. **Open and read the source.** Follow the source hierarchy in `CONTRIBUTING.md`: paper
   or proceedings, official project page, official repository, official docs, author/lab
   page, then a qualifying secondary explanation. Search snippets and submitted issue
   metadata are discovery aids, not verification. Confirm redirects lead to the same work.
3. **Identify the recursive mechanism.** State what calls itself, branches, revises its
   output using feedback, reuses reasoning states, or updates itself across iterations.
   Connect that mechanism to the resource's contribution. A generic LLM, RAG, agent
   framework, or social simulation does not qualify merely because it mentions agents
   or loops; recursion must be central under the README's taxonomy.
4. **Verify title and date.** Use the source's actual title and publication/release
   evidence. The inclusion window starts **15 May 2022**; a year alone cannot resolve
   a boundary case in 2022. Do not substitute a site's copyright or last-updated year.
   Older work may only be proposed as clearly marked, necessary historical context.
5. **Draft one unwrapped entry line** with the exact format below. Use a single hyphen
   separator, one concise sentence ending in a period, and the verified year at the end:

   ```markdown
   - [Resource title](URL) - One concise sentence on what it is and why it matters. (Year)
   ```

6. **Place and re-review it.** Choose the dominant recursive mechanism, compare with
   neighbouring entries, and verify every claim in the final wording against the source.
   Run the validation commands after the edit.

Keep a compact evidence note in the response or PR: source URL, verified title/date,
recursive mechanism, placement rationale, and duplicate-search result. Keep research
notes out of README entries. If any required fact is unverified, leave the candidate out
and identify the missing evidence; do not guess authors, venues, dates, benchmarks, or
results. Fix straightforward wording and formatting issues directly within the task.

## Taxonomy and README invariants

- Use the existing Taxonomy table as the placement rubric. Papers belong in the relevant
  topic or Core Papers; implementations in Open-Source Implementations; datasets and tasks
  in Benchmarks and Evaluation Tasks. Being new does not automatically make a paper core.
- Preserve related-work groupings. There is no blanket alphabetical or newest-first
  ordering rule. If placement is unclear or needs a new section, explain the proposal
  for maintainer review instead of forcing it into the list.
- Keep Contents aligned with section headings and anchors when headings change. Preserve
  the Awesome badge in the main heading. Follow the awesome-lint skill for special rules
  such as excluding Contributing and License from Contents.
- After moving or removing an entry, check prose cross-references and taxonomy examples
  for stale references. Avoid repeating URLs unnecessarily.
- Thin sections guide research, not quotas. Coverage reports should count resource entries,
  not Contents bullets or prose cross-references. A trailing year supports only approximate
  freshness; inspect source dates before making precise age claims.

## The curation pipeline

The assets declared in `apm.yml` define focused roles. Use the relevant procedure for
the task; a small edit does not require launching the entire pipeline.

| Role                                                         | Boundary and expected output                                                                                                                                             |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [paper-scout](.github/agents/paper-scout.agent.md)           | Read-only discovery: verified candidate table with URL, title, year, proposed section, and recursion rationale.                                                          |
| [curate-entry](.github/agents/curate-entry.agent.md)         | Vets and edits: minimal canonical entry diff plus eligibility and placement rationale.                                                                                   |
| [entry-reviewer](.github/agents/entry-reviewer.agent.md)     | Read-only review: independently verifies the changed entries and reports per-entry verdicts with source evidence.                                                        |
| [taxonomy-auditor](.github/agents/taxonomy-auditor.agent.md) | Checks placement, duplicates, ordering, and cross-references; produces coverage findings and may apply unambiguous fixes within scope. Proposes judgement-heavy changes. |

Supporting skills: [coverage-report](.github/skills/coverage-report/SKILL.md) for expansion
planning, [awesome-lint](.github/skills/awesome-lint/SKILL.md) for compliance diagnostics,
and [link-check](.github/skills/link-check/SKILL.md) for reachability and source identity.

## Editing boundaries

- Keep descriptions neutral and specific. Remove promotional, ranking, pricing, or
  time-sensitive claims unless necessary and directly supported; never copy an abstract
  without checking its relevance.
- Do **not** reformat or reflow `README.md`, `CONTRIBUTING.md`, or `CLAUDE.md` wholesale.
  They are excluded from Prettier intentionally. Avoid repository-wide `npm run format`
  for a small change; format only the files or blocks you edited when needed.
- Preserve UTF-8 text and avoid unrelated line-ending changes; use the formatter's line
  endings for files it covers. Check the final diff for encoding damage and unrelated
  changes, especially when editing through Windows shell commands.
- Shipped tooling lives under `.github/`. Do not force-add ignored root-level `agents/`,
  `skills/`, `hooks/`, `workflows/`, `plugins/`, or `instructions/`, or generated reports
  and local editor state. Update `apm.yml` if shipped asset paths change.
- Dependency changes must be intentional and keep `package.json` and `package-lock.json`
  consistent. Do not add runtime scaffolding or secrets to this documentation repository.

## Completion and review handoff

Before finishing, inspect `git diff --check`, `git diff --stat`, and the full relevant
diff. Confirm that only intended files changed and that linked local paths exist with
the correct casing for Linux CI.

The final response or PR should state:

- What changed and why it fits this repository; include evidence notes for entry changes.
- Which guidance was considered (`AGENTS.md`, `CONTRIBUTING.md`, `CLAUDE.md`, and relevant
  agent/skill files), and any unresolved eligibility or taxonomy question.
- Which checks ran and their actual outcomes, including warnings, failures, and checks
  not run. Do not describe skipped or network-blocked checks as passing.

Use the PR template when opening a PR and omit its entry checklist when entries are
untouched. Keep titles and commit subjects concise and descriptive. Maintainer notes
should identify concrete review decisions, with friendly explanations tied to the
contribution rules; the final curation decision rests with the human maintainer.
