# Contributing

Thank you for helping keep this list focused and useful.

## How to Contribute

- **Suggest a resource** — open an issue using the
  [Suggest a resource](https://github.com/natnew/awesome-recursive-language-models/issues/new?template=suggest-resource.yml)
  form. It collects everything needed to vet the resource against this document.
- **Report a broken link** — use the
  [Broken link](https://github.com/natnew/awesome-recursive-language-models/issues/new?template=broken-link.yml)
  form.
- **Open a pull request** — add the entry yourself following the rules below. The PR
  template includes the quality checklist, and CI validates formatting, Markdown style,
  awesome-list compliance, and link integrity.
- **Improve an existing entry or repository guidance** — correct wording, source links,
  taxonomy placement, documentation, or validation tooling with a focused explanation.
- **Report a security concern** — follow [SECURITY.md](SECURITY.md) for suspected malicious
  links, credential leaks, or vulnerable tooling. Keep sensitive details out of public issues.

You do not need to install any tools to suggest a resource or report a content problem.
Search existing entries and issues first, and include enough evidence for a maintainer
to evaluate the change. Small corrections can go straight to a PR; propose substantial
taxonomy or inclusion-policy changes in an issue before reorganising the list.

This repository also ships an agent-assisted curation pipeline (discovery, vetting,
review, and audit agents) described in [`AGENTS.md`](AGENTS.md); it applies the same
rules in this document.

## Purpose

This repository curates high-signal resources on recursive language models, recursive inference, recursive reasoning architectures, self-calling AI systems, and adjacent work where recursion is central to the method.

It also supports research into learned simulation engines for society: AI systems that can model social, institutional, and behavioural dynamics through recursive agents, simulated populations, evaluation loops, reinforcement learning, and inspectable long-horizon reasoning.

## Resource Inclusion Criteria

Contributions should satisfy all of the following:

- The resource is directly relevant to recursion in AI systems.
- Recursion is central to the method, architecture, inference process, evaluation design, agent loop, or self-improvement mechanism.
- The resource is technically credible and useful to researchers or builders.
- The source is preferably primary: arXiv, official project page, official GitHub repository, official documentation, author website, or conference page.
- The description is accurate, concise, and non-promotional.

Explain the mechanism, not just the topic: what calls itself, branches, reuses reasoning
states, revises output using feedback, or changes through a self-improvement loop?
Identify where the source describes it and why it is central to the contribution.
The [README taxonomy](README.md#taxonomy) includes iterative refinement and recurrent
architectures; an explicit self-call in code is not the only qualifying pattern.
Conversely, mentioning agents, simulation, or multiple model calls is not enough by itself.

## Time-Window Rule

Resources should be from 15 May 2022 onwards.

Older resources may only be proposed for a short historical context section if they are necessary for understanding the field. Mark them clearly as outside the main inclusion window.

Verify the publication or release date from the source. For work dated 2022, check the
month and day against the cutoff; do not infer eligibility from the year alone. A site's
copyright year or recent maintenance commit does not establish a resource's release date.
If a preprint and later publication have different dates, identify which version you are
linking and explain the choice in the PR. Leave uncertain dates unresolved rather than
guessing. A newer revision alone does not establish that an older resource meets the window.

## Link Verification

Before submitting a resource:

- Open the link.
- Confirm the page loads.
- Confirm the title on the page matches the proposed title.
- Confirm the linked source is the intended resource and follows the source hierarchy below.

Check redirect destinations and prefer a durable canonical URL. Search snippets, an
AI-generated summary, or a contributor's proposed title/year do not replace reading the
source. Verifying a resource does not require installing its code or running its examples.

For a broken-link fix, include the existing entry, what happens when you open it, and
why the proposed replacement is the same resource. A timeout, 403, or rate limit is not
proof that the work disappeared. Recheck before proposing removal; use the security
policy instead if the destination appears compromised.

## Description Accuracy

Descriptions should state what the resource is and why it matters for recursive language models or recursive agent systems.

Avoid:

- vague praise;
- unsupported claims;
- exaggerated importance;
- invented venues, authors, dates, benchmarks, or results;
- descriptions copied from abstracts without checking relevance.

Prefer concrete mechanisms over rankings, popularity, or claims such as "best" and
"state of the art". Keep source evidence and longer comparisons in the PR, not the list.

## Duplicate Prevention

Before adding a resource:

- Search the README for the title, project name, arXiv identifier, repository name, and common abbreviation.
- Do not add the same paper, repository, or project in multiple sections unless there is a strong reason.
- If a resource is relevant to another section, prefer a short cross-reference in prose rather than duplicating the entry.

Check alternate titles, abbreviations, arXiv versions, and repository URLs that identify
the same work. If a paper and its implementation merit separate entries, explain their
distinct usefulness instead of repeating the same description or adding a second entry
only to increase coverage.

## Section Placement

Use the existing Contents and Taxonomy in `README.md` as the section map. Place a paper
by its dominant recursive mechanism; implementations usually belong in Open-Source
Implementations, and datasets or tasks in Benchmarks and Evaluation Tasks. Core Papers
is not a catch-all for new papers.

Preserve the existing related-work groupings; there is no blanket alphabetical or
newest-first ordering requirement. If placement is unclear, propose a section and give
your reasoning in the issue or PR. Thin sections are research opportunities, not quotas.
When moving entries, check prose cross-references and taxonomy examples. When changing
headings, update Contents and anchors together.

## Preferred Source Hierarchy

Use the most authoritative available source:

1. arXiv paper, conference page, or official proceedings page.
2. Official project page.
3. Official GitHub repository.
4. Official documentation.
5. Author or lab page.
6. High-quality secondary explanation, only when it adds clear value and the primary source is also listed or unavailable.

## Suggested Contribution Format

Use this format:

```markdown
- [Resource title](URL) - One concise sentence explaining what it is and why it matters. (Year)
```

Keep each entry on one unwrapped line. Use a single hyphen separator with spaces,
end the description with a period, and put the verified year in parentheses at the end.
The linked title should match the source, including subtitles that affect its meaning.

Example:

```markdown
- [Tree of Thoughts: Deliberate Problem Solving with Large Language Models](https://arxiv.org/abs/2305.10601) - Frames reasoning as search over intermediate thought states with generation, self-evaluation, and selection. (2023)
```

## Quality Checklist

Before submitting, confirm:

- The resource is within the inclusion time window (15 May 2022 onwards) or clearly marked as historical context.
- The link works.
- The title matches the linked page.
- The description is accurate.
- The resource is not already listed.
- The resource is directly relevant to recursion in AI systems.
- The resource is not merely a general LLM, prompt engineering, RAG, or agents resource.
- The resource supports the repository's technical purpose.
- The year is correct.
- No duplicate entry has been introduced.

## Preparing a Pull Request

1. Work on a branch in your fork or checkout. Keep unrelated fixes in separate PRs and
   preserve other contributors' changes.
2. Read the target section and verify the resource before writing the entry. Use the
   [PR template](.github/PULL_REQUEST_TEMPLATE.md); omit the entry checklist for changes
   that do not touch entries.
3. Include a short evidence note for each added or substantially changed resource:
   source URL, verified title/date, recursive mechanism, proposed section, and duplicate
   search result. Explain any historical-context or secondary-source exception.
4. Run the checks below and review the diff for unrelated formatting, encoding damage,
   and broken local links. Report commands, results, and any checks you could not run.

AI-assisted contributions follow the same rules. You remain responsible for reading
sources, checking claims, and reviewing the final diff; generated citations and a passing
linter do not establish scientific accuracy. [AGENTS.md](AGENTS.md) describes the agent
workflow, and `CLAUDE.md` provides companion guidance for Claude Code.

Keep README and this file's hand-curated formatting. Do not run a formatter over them
wholesale, reorder unrelated sections, or add screenshots and research notes to list
entries. Do not commit ignored local tooling directories or generated reports. Changes
to development dependencies must keep `package.json` and `package-lock.json` consistent;
changes to shipped agent asset paths must also update `apm.yml`.

## Out-of-Scope Resources

Do not add:

- generic LLM papers without an explicit recursive mechanism;
- general prompt engineering resources;
- general RAG resources where recursive retrieval, summarisation, or decomposition is not central;
- broad AI agent lists or frameworks without recursive planning, reflection, self-correction, or tool-use loops;
- unverified blog posts, newsletters, or social-media summaries;
- resources with broken links;
- resources whose date cannot be verified;
- resources whose claims cannot be matched to the linked source.

## Validation

For local validation, use Node.js 22 (the CI version) and npm. From the repository root,
install the locked development dependencies on a fresh checkout or after lockfile changes:

```bash
npm ci
```

Then run all five checks, including for documentation-only PRs:

```bash
npm run build          # Prettier formatting check; does not build an application
npm run lint           # Markdown style for included repository files
npm run lint:awesome   # awesome-list compliance for README.md
npm test               # README link reachability
npm run lint:docs      # Remark checks on the five root guidance/list documents
```

Understand the checks' limits:

- Prettier excludes `README.md`, this file, and `CLAUDE.md`; Markdown lint excludes
  `README.md` and this file. Preserve their formatting manually.
- The link test skips this repository's own GitHub URLs and does not verify source
  claims. Manually check changed self-links, section anchors, and links in other documents.
- Docs lint can exit successfully with warnings. Inspect its output; the current Remark
  indentation rule disagrees with Prettier's list formatting. Report that mismatch without
  suppressing rules or reformatting the whole list to silence it.
- On Windows, CRLF checkout line endings can cause Prettier failures in untouched files.
  Compare the diff with the committed content before treating them as content defects.

Fix failures introduced by your change. For existing failures or network restrictions,
include the exact command and a concise diagnostic; do not report blocked checks as
passing or remove good resources to satisfy a transient network failure. If you cannot
run the tools, submit a resource suggestion or clearly mark a PR as needing validation.

[CI](.github/workflows/ci.yml) also installs and audits APM assets and runs the AgentRC
readiness gate. These must pass before merge; local npm checks alone do not establish
that the entire CI workflow passed. No application server or runtime secrets are needed
for local content validation.

## Review Standard

This list should remain concise, technically credible, and research-oriented. A smaller set of well-verified resources is preferable to broad coverage with weak relevance.

Maintainers may correct small wording, formatting, or placement issues directly. They
may request evidence, suggest a cross-reference for a duplicate, defer a borderline
resource for discussion, or decline work that does not meet the criteria. Clear reasons
and links to the relevant rule help contributors improve a proposal. Passing CI is
necessary but does not guarantee inclusion; the final curation decision rests with the
maintainer. Disclose an author or project affiliation when it helps reviewers understand
your suggestion; affiliated submissions are evaluated by the same criteria.

## Licensing

This repository is released under [CC0 1.0](LICENSE). By contributing, you agree that
your contributions are released under the same terms.
