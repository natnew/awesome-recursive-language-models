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

## Time-Window Rule

Resources should be from 15 May 2022 onwards.

Older resources may only be proposed for a short historical context section if they are necessary for understanding the field. Mark them clearly as outside the main inclusion window.

## Link Verification

Before submitting a resource:

- Open the link.
- Confirm the page loads.
- Confirm the title on the page matches the proposed title.
- Confirm the linked source is the intended resource, not a secondary summary unless no primary source exists.

## Description Accuracy

Descriptions should state what the resource is and why it matters for recursive language models or recursive agent systems.

Avoid:

- vague praise;
- unsupported claims;
- exaggerated importance;
- invented venues, authors, dates, benchmarks, or results;
- descriptions copied from abstracts without checking relevance.

## Duplicate Prevention

Before adding a resource:

- Search the README for the title, project name, arXiv identifier, repository name, and common abbreviation.
- Do not add the same paper, repository, or project in multiple sections unless there is a strong reason.
- If a resource is relevant to another section, prefer a short cross-reference in prose rather than duplicating the entry.

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

Before opening a pull request, run the same checks CI runs:

```bash
npm ci                 # install dev tooling
npm run lint           # markdownlint
npm run lint:awesome   # awesome-list compliance for README.md
npm test               # link check (linkinator)
```

All three checks must pass. Keep diffs minimal: `README.md` and this file are
hand-curated and must not be wholesale reformatted.

## Review Standard

This list should remain concise, technically credible, and research-oriented. A smaller set of well-verified resources is preferable to broad coverage with weak relevance.

## Licensing

This repository is released under [CC0 1.0](LICENSE). By contributing, you agree that
your contributions are released under the same terms.
