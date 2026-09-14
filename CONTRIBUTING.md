# Contributing

Thanks for your interest in the Semrush MCP Skills repository.

## Who can contribute

This repository is currently maintained by the Semrush MCP team, and **we are not accepting external pull requests yet
**. Pull requests from outside Semrush will be closed with a pointer to this page.

Issues, however, are very welcome. If you want to help, open a GitHub issue to:

- report a skill that produces wrong, outdated, or unhelpful results;
- suggest a new skill or an improvement to an existing one;
- flag unclear instructions, broken links, or errors in the documentation.

Please include the skill name, the agent you used, and what you expected to happen. We read every issue, and good
suggestions get built.

We plan to open the repository to external pull requests later. This page will be updated when that happens.

## How a change reaches the repository

For Semrush maintainers:

1. **Open an issue first** for anything beyond a typo fix, so the change can be discussed before work starts.
2. **Create a branch** from `main` and make your change there.
3. **Open a pull request** describing what the skill does, what changed, and how you tested it with a real agent.
4. **Review.** Every pull request needs approval from the Semrush MCP team before it can be merged. Reviewers check that
   the skill works end to end against the Semrush MCP server, that the instructions are clear to an agent, and that the
   content boundaries below are respected.
5. **Merge.** A maintainer merges the pull request once it is approved.

## What may never be added

Everything in this repository is public. Before you open a pull request, make sure your change contains **none** of the
following:

- **Internal service names, hostnames, endpoints, infrastructure or architecture details.** Only publicly documented MCP
  endpoints may appear.
- **MCP tools or parameters that are not publicly documented.** Reference only what is described in
  the [Semrush MCP documentation](https://developer.semrush.com/api/v4/introduction/semrush-mcp/).
- **Non-public product logic** — undocumented behavior, internal scoring or ranking methodology, roadmap or unreleased
  functionality.
- **Credentials of any kind** — API keys, tokens, passwords, OAuth secrets, or example values that resemble real ones.
- **Customer data** — real domains, projects, reports, exports, or screenshots taken from a customer account. Use
  neutral placeholders such as `example.com` instead.

If you are unsure whether something falls into one of these categories, leave it out and raise it in the pull request.

## Writing a skill

Each skill lives in its own folder in the repository root, named in lowercase with hyphens (for example,
`technical-seo-audit/`). The folder contains a `SKILL.md` file with the workflow the agent follows, plus any supporting
files the skill needs.

### Required frontmatter

Every `SKILL.md` must begin with a YAML frontmatter block containing `name` and `description`:

```markdown
---
name: technical-seo-audit
description: Audits a domain for crawlability, Core Web Vitals, schema, and on-page issues using Semrush data. Use when the user asks for a technical SEO audit, a site health check, or wants to know why a site is not ranking for technical reasons.
---
```

- `name` — lowercase letters, digits and hyphens only, up to 64 characters. **It must match the folder name exactly**,
  or the skill will not install or load correctly.
- `description` — up to 1024 characters.

Write the `description` for the agent, not for a human browsing the repository. At the start of a session, an agent
loads only the `name` and `description` of each installed skill and uses them to decide which skill a request matches;
it does not read the body until the skill is activated. A description that explains only *what* the skill does will
rarely trigger. Cover both **what the skill does** and **when to use it**, including the phrases a user is likely to
say.

Keep the body of `SKILL.md` focused — roughly 500 lines or fewer. Move long reference material into separate files in
the skill folder and link to them, so the agent loads them only when it needs them.

### What makes a good skill

A good skill:

- solves one clearly scoped task;
- gives the agent an explicit, ordered workflow rather than general advice;
- states which Semrush MCP tools it uses and when;
- tells the agent what to do when data is missing or a call fails;
- avoids inventing facts the data does not support.

Test your skill with at least one agent end to end before opening a pull request.

## License

By contributing to this repository, you agree that your contributions are licensed under
the [Apache License 2.0](LICENSE), the same license that covers this project.
