# Semrush MCP Skills

A collection of Agent Skills that give AI agents — Claude, ChatGPT, Codex, Cursor, and other Agent Skills-compatible
tools — reusable SEO workflows built on the Semrush MCP server.

## What is a skill?

A skill is a self-contained Markdown instruction set that teaches an AI agent how to complete one specific task, such as
running a technical SEO audit or building a content brief. Each skill lives in its own folder in this repository and
contains a `SKILL.md` file with the workflow the agent follows. There is no service code here — only instructions.

Skills are designed to be used together with the Semrush MCP server: the skill defines *the workflow*, and the MCP
server provides the underlying SEO data and tools. Once an agent has a skill loaded, it applies the same repeatable
process every time instead of improvising a new approach.

## Available skills

| Category              | Skill                                       | What it does                                                                                       |
|-----------------------|---------------------------------------------|----------------------------------------------------------------------------------------------------|
| Technical SEO         | [technical-seo-audit](technical-seo-audit/) | Audit crawlability, Core Web Vitals, schema, and on-page signals in one pass                       |
| Technical SEO         | [internal-link-audit](internal-link-audit/) | Find orphan pages, broken internal links, depth issues, and missing hubs                           |
| Technical SEO         | [schema-markup](schema-markup/)             | Audit, draft, and validate structured data without inventing entity facts                          |                      |
| Keyword Research      | [keyword-research](keyword-research/)       | Find keyword ideas with volume, difficulty, intent, and CPC, clustered by topic                    |
| Keyword Research      | [content-brief](content-brief/)             | Turn one keyword into a brief a writer can ship: intent, SERP context, outline, FAQs, linking plan |
| Rankings & SERPs      | [serp-analysis](serp-analysis/)             | Analyze the top 10 for any keyword: format, features, gaps, ranking strategy                       |
| Backlinks & Authority | [backlink-audit](backlink-audit/)           | Audit a backlink profile: anchor distribution, toxicity, competitor gaps, broken-link recovery     |
| Competitor Research   | [competitor-gap](competitor-gap/)           | Find keyword, content, and link gaps between your domain and your real search competitors          |

## Installing a skill

### Prerequisite: connect Semrush MCP

These skills call Semrush data through the Semrush MCP server. Connect it in your agent first — setup instructions for
Claude, Claude Code, ChatGPT, Cursor, VS Code, Perplexity and others are in
the [Semrush MCP documentation](https://developer.semrush.com/api/v4/introduction/semrush-mcp/). Using Semrush MCP
requires an eligible Semrush subscription with API access.

### Install all skills

```
npx skills add semrush/skills
```

### Install a single skill

```
npx skills add semrush/skills/technical-seo-audit
```

### Install manually

Copy the skill's folder into your agent's skills directory (for example, `.claude/skills/` for Claude Code), then
restart the agent so it picks up the new skill.

## Using a skill

Once a skill is installed and Semrush MCP is connected, describe the task in plain language — for example, *"run a
technical SEO audit on example.com"* — and the agent will follow the skill's workflow, pulling live data from Semrush as
it goes.

AI responses may be incomplete or inaccurate. Verify results before using them for decisions, publication, or other
critical work.

## License

Licensed under the [Apache License 2.0](LICENSE). See [NOTICE](NOTICE) for attribution requirements.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how changes to this repository are reviewed and approved.
