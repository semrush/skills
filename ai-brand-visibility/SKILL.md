---
name: ai-brand-visibility
description: Measure how a brand appears in AI answers by combining Semrush AI-channel traffic estimates with controlled prompt observations, keeping measured findings separate from diagnostic hypotheses. Use when the user asks about AI visibility, whether ChatGPT or Perplexity mention their brand, AI share of voice, or how much traffic arrives from AI assistants. AI-channel traffic reports require a Trends subscription.
---

# AI brand visibility

Measure how a brand appears in selected AI answers, what traffic arrives from AI channels, and which evidence-backed actions may improve visibility. Traditional rankings, AI referral traffic, prompt mentions, and citations are related but different signals.

## Rule provenance

- **Semrush-supported guidance:** measure mentions, citations, sentiment, AI share of voice, referral traffic, and cited sources; use prompts across the customer journey; improve accessibility, clarity, original value, freshness, brand consistency, and credible third-party presence.
- **MCP contract requirement:** the tested public MCP exposes AI-assistant and AI-search traffic estimates plus organic/SERP context. It does not expose prompt responses, brand mentions, citations, sentiment, prompt-level positions, or AI share of voice.
- **Measurement definition:** any custom mention rate, citation rate, competitor share, or sentiment label must show its formula and tested sample.
- **Industry heuristic:** diagnosis and prioritization are analyst judgments unless a controlled test or user data supports them.
- **User-configurable default:** platforms, prompts, markets, devices, cadence, and sample size must fit the audience and decision. No universal prompt count or change threshold applies.

## Inputs

Ask once for:

- brand name, domain, products, audience, and market;
- business questions or journey stages the user wants to measure;
- relevant competitors, if comparison is in scope;
- target AI platforms and any platform/model/account constraints;
- an existing prompt list or first-party sources such as customer research, sales calls, support tickets, Search Console exports, or analytics;
- any Semrush AI Visibility Toolkit or Enterprise AIO export the user can supply.

Do not ask for a Semrush API key. The official MCP uses Semrush authentication.

## Public MCP capability boundary

Discover the live tools and schemas before execution.

### `traffic_overview`

- `summary`: request total traffic plus `ai_assistants` and `ai_search` for the brand and, when useful, competitors.
- `sources`: filter `traffic_channel` to `ai_assistants` or `ai_search` to retrieve estimated traffic by referrer or search engine.
- `toppages`: request page-level traffic with `ai_assistants` and `ai_search` to see which URLs receive estimated visits from those channels.

These are traffic estimates. They do not show whether a brand was mentioned without a click, which prompt produced a visit, what an AI answer said, or which page was cited but not clicked.

Traffic and audience reports require the corresponding Trends subscription. If access is unavailable, use a supplied export or mark those comparisons unavailable. Do not substitute organic-search estimates.

### Search context

- `domain_overview` → `domain_rank`: use organic totals and explicitly requested AI Overview SERP-feature fields as Google search context.
- `organic_research` → `resource_organic`: use ranking keywords, URLs, and returned SERP-feature codes as search context.

AI Overview keyword/position totals are not LLM brand mentions, AI citations, or cross-platform share of voice.

### Unsupported prompt-level metrics

The tested public discovery did not expose AI Visibility Toolkit or Enterprise AIO reports for prompt responses, mentions, citations, sentiment, source visibility, or share of voice. Never manufacture those metrics from Traffic Analytics, Organic Research, or manual spot checks.

If the user supplies a product export, preserve the product's definitions and label the source. Otherwise use the controlled manual protocol below.

## Access and evidence guardrails

- Tell the user that Semrush calls may consume API units. Use the smallest set that answers the question, then expand when requested.
- Label Semrush Traffic Analytics and organic figures as estimates.
- Separate Semrush estimates, product exports, first-party analytics, manual prompt observations, direct page/crawler checks, and model inference.
- Manual AI answers can vary with model version, account, location, personalization, browsing mode, and time. A single response is an observation, not a stable platform-wide result.
- Do not imply that AI traffic equals AI visibility or that organic rank guarantees mention/citation.
- Do not promise a ranking, citation, mention, traffic, revenue, or delivery timeline.

## Fallback ladder

1. Supplied AI Visibility Toolkit or Enterprise AIO export for dedicated prompt metrics.
2. Official Semrush MCP for AI traffic estimates and search context.
3. First-party analytics for observed AI referrals.
4. Controlled manual prompt testing across selected platforms.
5. Technical, content, and third-party presence review. Label this diagnostic, not measured visibility.

## Workflow

### 1. Define the measurement question

Choose the prompts and platforms from the audience's real use cases. Include the journey stages relevant to the user's goal:

- **Research:** definitions, problems, methods, and best practices.
- **Comparison:** categories, alternatives, and option tradeoffs.
- **Evaluation:** brand capabilities, pricing, fit, limitations, and brand-versus-brand questions.

Do not default to bottom-of-funnel prompts only. Research prompts can reveal citations and category association even when they do not name vendors.

Source prompt candidates from first-party language, supplied search data, relevant PAA questions, and legitimate community research. Add constraints only when they reflect real audience needs; do not engineer prompts merely to force the brand into an answer.

Document why each prompt is in the sample. Let the user choose coverage depth based on decision importance and cost.

### 2. Establish Semrush context

When Trends access exists:

1. run `summary` for the brand and relevant competitors with `ai_assistants` and `ai_search`;
2. run `sources` separately for the two AI traffic channels;
3. run `toppages` to identify URLs receiving estimated AI-channel visits;
4. retain date, country, device, accuracy value, and fields returned.

Optionally run `domain_rank` or `resource_organic` for traditional search and AI Overview SERP context. Keep that layer separate from prompt testing.

### 3. Run a controlled prompt sample

For every prompt/platform observation, record:

- exact prompt;
- platform, product surface, model/version when visible, and browsing/search mode;
- date/time, country, language, account state, and whether the session was fresh;
- full response or durable capture;
- response completion or finish status, including empty or truncated output;
- brand mentions and the exact surrounding wording;
- links/citations and confirmed destination URLs; resolve citation redirects when possible, and mark the destination unresolved when it cannot be verified;
- order of named brands when meaningful;
- factual claims about the brand and whether they are correct;
- competitors mentioned;
- limitations or failed runs.

Use fresh sessions where feasible and apply the same protocol to competitors. Do not pretend fresh sessions eliminate all variability. Repeat observations when the decision requires reliability, and preserve every run rather than keeping only favorable answers.

Define a valid observation before calculating metrics. At minimum, require a non-empty, completed answer that can be attributed to the recorded platform and prompt. Keep empty, truncated, blocked, timed-out, or otherwise failed attempts in the evidence log, but exclude them from mention, citation, and accuracy denominators. A retry is a new observation; it does not overwrite the failed attempt.

### 4. Calculate transparent sample metrics

Use only metrics the evidence supports. Examples:

- **Mention rate:** valid prompt-platform observations containing the brand ÷ all valid observations in the defined sample.
- **Citation rate:** valid observations with a confirmed citation destination on the brand's domain ÷ all valid observations in the sample. Do not count unresolved redirect or proxy URLs as brand citations.
- **Competitor mention share:** the brand's mentions ÷ mentions of all named brands in the defined comparison set.
- **Factual accuracy rate:** correct brand claims ÷ verifiable brand claims reviewed.

Do not call a custom metric “Semrush AI Share of Voice.” Name it as a sample metric and show the formula, denominator, platforms, prompt set, and dates.

Treat sentiment and prominence as coded judgments. Define the coding rubric, retain the supporting excerpt, and allow human review. Do not assume the first-listed brand receives a fixed benefit.

### 5. Diagnose gaps

Tie every diagnosis to observed evidence.

#### Accessibility and crawler controls

Delegate the full check to `technical-seo-audit`.

- `OAI-SearchBot` controls automatic crawling for ChatGPT search inclusion.
- `GPTBot` controls potential training use and is independent of ChatGPT Search.
- `Google-Extended` does not control Google Search inclusion or rankings.

Blocking a training crawler is not automatically an AI visibility defect. Verify other platforms through current first-party documentation.

#### Content and entity clarity

Review cited, high-AI-traffic, or strategically important pages for accurate brand/product descriptions, direct answers, clear headings, evidence, original data or experience, source quality, and current facts. Do not enforce paragraph, word-count, heading-count, comparison-table, or freshness-age formulas.

#### Third-party corroboration

Review the actual domains and pages cited for the prompt set, plus relevant linked and unlinked brand mentions supplied by approved tools or research. Assess topical relevance, editorial credibility, accuracy, and consistency.

Do not manufacture or seed branded recommendations on Reddit, Quora, or other communities. Legitimate participation means answering real questions transparently, following platform rules, disclosing affiliation, and contributing value without coordinated manipulation.

#### Search and traffic context

Use organic rankings, AI Overview fields, backlinks, and AI referral traffic to explain context—not causation. Low or high traffic and keyword counts do not prove why an AI system did or did not mention a brand.

### 6. Recommend and retest

For each action, identify:

- the prompt or evidence gap;
- the page, claim, source, or technical control involved;
- what should change;
- the owner;
- the metric and protocol for retesting;
- confidence and dependencies.

Retest on a cadence appropriate to the decision and platform volatility. Compare like-for-like prompt sets and clearly disclose any platform, model, market, or sample changes.

## Output

### Evidence coverage

| Evidence class | Source | Scope/date | What it measures | What it does not measure |
| -------------- | ------ | ---------- | ---------------- | ------------------------ |

### Semrush traffic context

| Target | Total estimated visits | AI-assistant visits | AI-search visits | Country/device/date | Accuracy |
| ------ | ---------------------: | ------------------: | ---------------: | ------------------- | -------- |

### Prompt observations

| Prompt | Stage | Platform/model | Mention | Citation URL | Brand wording | Accuracy | Competitors | Evidence date |
| ------ | ----- | -------------- | ------- | ------------ | ------------- | -------- | ----------- | ------------- |

### Sample metrics

| Metric | Formula | Result | Sample definition | Limitations |
| ------ | ------- | -----: | ----------------- | ----------- |

### Actions

| Priority | Evidence gap | Asset/control | Action | Owner | Retest metric | Confidence |
| -------- | ------------ | ------------- | ------ | ----- | ------------- | ---------- |

End with:

1. **Confirmed:** measured mentions, citations, traffic, or factual errors.
2. **Improve:** actions directly tied to the evidence.
3. **Validate:** diagnostic hypotheses and variable manual observations.
4. **Unavailable:** prompt-level product metrics or other data not supplied.

## Sources

Semrush methodology:

- [Generative Engine Optimization](https://www.semrush.com/blog/generative-engine-optimization/)
- [AI Visibility](https://www.semrush.com/blog/ai-visibility/)
- [How to Rank in AI Search](https://www.semrush.com/blog/how-to-rank-in-ai-search/)
- [AI Search Visibility Study](https://www.semrush.com/blog/ai-search-visibility-study-findings/)
- [LLM Optimization](https://www.semrush.com/blog/llm-optimization/)
- [LLM Monitoring Tools](https://www.semrush.com/blog/llm-monitoring-tools/)
- [Brand Visibility in AI Search](https://www.semrush.com/blog/brand-visibility/)
- [Optimize Content for AI Search Engines](https://www.semrush.com/blog/how-to-optimize-content-for-ai-search-engines/)

Primary crawler references:

- [OpenAI crawlers](https://developers.openai.com/api/docs/bots)
- [Google crawler controls](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers)
