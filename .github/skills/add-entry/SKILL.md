---
name: add-entry
description: End-to-end procedure for adding one resource to the list — duplicate search, source verification, canonical formatting, section placement, and validation. Use whenever a new entry is being added to README.md.
---

# Add Entry Skill

Adds a single resource to `README.md` for the **awesome-recursive-language-models** list.
The rules live in [`CONTRIBUTING.md`](../../../CONTRIBUTING.md); this skill is the order
of operations. For vetting judgement calls, defer to the
[`curate-entry`](../../agents/curate-entry.agent.md) agent.

## Procedure

1. **Search for duplicates first.** Grep `README.md` for the title, project name, arXiv
   id, repository name, and common abbreviation. If found, stop — propose a prose
   cross-reference instead.

2. **Verify the source.** Open the URL. Confirm it loads, is the most primary source
   available (arXiv / official project page / official repo / docs / author page), and
   read the exact title and publication year from the page itself.

3. **Check eligibility.** Recursion central, not incidental; within the 15 May 2022
   window (or marked historical); not a generic LLM / prompt-engineering / RAG / broad
   agent-framework resource.

4. **Write the entry** in the canonical format — one line, no wrapping:

   ```markdown
   - [Resource title](URL) - One concise, accurate sentence on what it is and why it matters for recursion in AI systems. (Year)
   ```

5. **Place it** in the taxonomy section that best matches its recursive mechanism (the
   Taxonomy table at the top of `README.md` is the rubric). Edit only the lines you are
   adding — `README.md` is hand-curated and excluded from Prettier.

6. **Validate:**

   ```bash
   npm run lint           # markdownlint
   npm run lint:awesome   # awesome-list compliance
   npm test               # linkinator — the new link must resolve
   ```

## Output

A minimal diff adding exactly one list line, with all three validation commands passing.
