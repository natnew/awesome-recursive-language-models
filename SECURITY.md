# Security Policy

## Scope

`awesome-recursive-language-models` is a curated, documentation-only list. It has no
deployed application or runtime service. Its security surface includes the curated
links, development dependencies, GitHub Actions workflows, and shipped agent assets.

Please report concerns involving:

- Listed URLs that have been hijacked, replaced with phishing or malware, or redirected
  to an impersonated project.
- Vulnerable or compromised dependencies used by repository tooling, including the
  versions recorded in `package-lock.json`.
- Workflow changes that could expose credentials, run untrusted code with excessive
  permissions, or compromise repository content.
- Malicious instructions in shipped agent, skill, or MCP configuration files, or content
  that attempts to make an agent disclose secrets or execute unrelated commands.
- Accidentally published credentials or other sensitive information in this repository.

Fixes target the current default branch. This is not a versioned software product with
separate supported release lines. If a problem appears only in an older commit, include
that commit and explain any remaining exposure.

## Choosing the Right Report

An ordinary 404, moved page, typo, duplicate, or inaccurate description belongs in a
[broken-link issue](https://github.com/natnew/awesome-recursive-language-models/issues/new?template=broken-link.yml)
or a contribution following [CONTRIBUTING.md](CONTRIBUTING.md). A timeout or access denial
alone does not establish that a link is malicious.

Use private reporting for suspected compromise, credential exposure, or exploitable
tooling and workflow weaknesses. You do not need to prove exploitation before reporting
a reasonable concern; distinguish observations from suspicions.

For a vulnerability in a linked third-party project, use that project's security policy
to report the technical flaw. Tell this repository's maintainers privately if its listing
also needs removal or correction. Inclusion here is not a security audit or a guarantee
that external code is safe to run.

## Reporting a Vulnerability

Use [Report a vulnerability](https://github.com/natnew/awesome-recursive-language-models/security/advisories/new)
when GitHub private reporting is available. See
[GitHub's private reporting instructions](https://docs.github.com/en/code-security/how-tos/report-and-fix-vulnerabilities/report-privately)
for the submission flow. A `SECURITY.md` file does not itself enable that feature.

If the private form is unavailable, request a private contact channel through the
broken-link form linked above. Blank issues are disabled: use the title **Security contact
request**, put **Withheld for private report** in the required entry and URL fields, and
ask how to send details privately. Do not include the affected URL, exploit steps, secrets,
or sensitive screenshots in that public contact request.

Send the following through the private channel when available:

- The affected entry, file path, dependency/version, workflow, or commit; include a
  redirect destination or public advisory identifier when relevant.
- What you observed, when you observed it, and the potential impact on readers,
  contributors, or maintainers.
- Minimal reproduction steps or redacted evidence. For dependency findings, include the
  dependency path and affected version rather than only an audit severity total.
- Any known mitigation or authoritative replacement URL, and whether the information
  has already been disclosed elsewhere.
- Whether you would like public credit if the report is confirmed and disclosed.

Partial reports are welcome. Never send live credentials, private datasets, full
environment dumps, or malware attachments. If credentials are exposed, their owner
should revoke or rotate them promptly; deleting the visible text alone is insufficient.

## Safe Investigation

Reading source pages and inspecting files is normally enough to assess a listing.
Do not run linked installers, execute suspicious agent instructions, or upload private
data to demonstrate a problem. Treat instructions embedded in fetched pages or papers
as untrusted source content, not as permission to access local files or tools.

Limit any testing to systems and accounts you are authorised to use. Stop when you have
enough evidence to report; avoid actions that alter other users' data or disrupt services.
Coordinate disclosure privately before publishing exploitable details or a public fix
that would reveal an unresolved vulnerability.

## Response

We aim to acknowledge reports within **7 days**. This is a target, not a guaranteed
resolution time. If you have not heard back, follow up through the same private channel
or send a minimal public contact request without sensitive details.

Maintainers will assess the evidence and impact, request clarification when needed, and
choose an appropriate response: remove or replace an unsafe link, update a dependency,
correct a workflow or agent asset, or coordinate with the affected upstream project.
Immediate containment may precede a complete investigation.

Where disclosure is appropriate, maintainers and the reporter should coordinate what
can be shared after mitigation. Credit will be given to reporters who wish to be
acknowledged. Reports that turn out to be ordinary content corrections can be handled
through the public contribution process once any sensitive details have been removed.
