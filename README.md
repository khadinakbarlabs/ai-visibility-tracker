# AI Visibility Tracker

A **skills-only plugin** that uses the separately installed official **Apify CLI**, following Postiz's skill-to-CLI pattern. Its citation workflow runs [Khadin Akbar's AI Search Visibility Tracker](https://apify.com/khadinakbar/ai-search-visibility-tracker) to measure domain/page citations, citation position, content gaps and competing domains in AI search answers.

Nine coordinated skills cover SEO campaign orchestration, AI citation baselines and comparisons, competitor traffic and Google rankings, keyword opportunities, search trends, backlink samples, link prospects, and one evidence-linked action plan. The package includes no executable scripts, server, MCP connection, hooks, npm package or bundled dependencies.

## Requirements

Use a host with shell execution and internet access, the official `apify-cli` providing `apify api`, `jq`, and your authenticated Apify account. Apify charges apply. No separate AI-provider keys are supplied by this plugin. A chat surface without command execution can analyze a supplied export or provide a plan but cannot run the CLI.

If needed, install the official CLI with `npm install -g apify-cli`, then complete `apify login` in your own terminal. Keep your API token in Apify's local authentication flow; do not paste it into chat or package files. Verify with `apify info > /dev/null`.

## Use

Start with `$seo-growth-agent` on OpenAI/Codex or `/ai-visibility-tracker:seo-growth-agent` on Claude Code for the complete campaign. Specialist skills are roles guided by the host, not separate bundled processes.

OpenAI/Codex: invoke `$ai-visibility-tracker`, `$visibility-trends` or `$visibility-action-plan`, or describe your goal naturally.

Claude Code: invoke `/ai-visibility-tracker:ai-visibility-tracker`, `/ai-visibility-tracker:visibility-trends` or `/ai-visibility-tracker:visibility-action-plan`. To test a source folder without installing, launch `claude --plugin-dir /path/to/ai-visibility-tracker`.

Examples:

- “Check whether ChatGPT, Perplexity and Gemini cite ahrefs.com for backlink research. Use these two exact buyer questions, with a $2 run budget.”
- “Compare these two saved citation checks and show which page citations were gained or lost.”
- “Create a content plan for topics where competing domains were cited and my site was absent.”

The main skill prepares input and checks current pricing before a billable run. Exact questions use `queryTemplates: []`; this Actor repeats them unchanged for each keyword. See the [Actor contract](skills/ai-visibility-tracker/references/actor-contract.md) and [CLI workflow](skills/ai-visibility-tracker/references/cli-workflow.md).

## Specialist workflows

| Skill | Purpose |
| --- | --- |
| seo-growth-agent | Intake, shared budget, routing and campaign continuity |
| ai-visibility-tracker | AI domain and page citation baseline |
| visibility-trends | Compare matching saved AI citation panels |
| competitor-intelligence | Competitor discovery, traffic estimates and Google ranks |
| keyword-opportunities | Keyword ideas, search demand and available difficulty |
| search-trends | Seasonality and relative search interest |
| competitor-backlinks | Compare capped backlink samples |
| link-opportunities | Qualify prospects using backlinks and AI citation sources |
| visibility-action-plan | Combine evidence into one prioritized action queue |

Read the [mapped Actor contracts](skills/seo-growth-agent/references/actor-contracts.md) and [campaign execution rules](skills/seo-growth-agent/references/execution.md). Live specialist research uses seven additional mapped Apify Actors. Examples do not authorize spending; the campaign shares one total cap. Traffic is estimated, Trends are normalized, and backlink samples are incomplete. Results cannot guarantee improved ranks or AI citations. AI content detection is outside this release.

## Distribution

The OpenAI export contains the portable root manifest and a synchronized Codex compatibility manifest. The Anthropic export contains only its native `.claude-plugin/plugin.json` manifest. Both include the same skills and references; only the OpenAI export includes `agents/openai.yaml` UI metadata. Archives isolate the provider-specific files.

Host installation does not create paid runs or schedules. A verified local package is distinct from public directory approval. Public listings require real publisher, policy/support URLs, permitted availability and platform review; missing declarations are not fabricated.

## Data and limits

Topics, domain and optional page/competitor targets are sent through the CLI to Apify for the requested Actor. Credentials remain managed by the independently installed CLI. Results and run records live in your Apify account; local exports belong in a private directory outside this package. Do not submit personal, confidential or customer data as AI search prompts.

Citation measurements are sampled API observations, not universal rankings across consumer apps. Missing/diagnostic results are unknown, citation position refers to the source list, and observed changes do not establish causation. No sentiment or brand-mention metrics are claimed for this Actor. Recurring tracking needs a separately configured, verified durable schedule and spend budget.

## Product pages

Maintained by Khadin Akbar. See the [product website](https://github.com/khadinakbarlabs/ai-visibility-tracker-docs), [support page](https://github.com/khadinakbarlabs/ai-visibility-tracker-docs/blob/main/SUPPORT.md), [privacy notice](https://github.com/khadinakbarlabs/ai-visibility-tracker-docs/blob/main/PRIVACY.md) and [terms of use](https://github.com/khadinakbarlabs/ai-visibility-tracker-docs/blob/main/TERMS.md).

## User-owned credentials

Every live user must supply their own Apify API token through the official local `apify login` flow or their host's supported secret storage. Authenticate only to that user's account. Never use, bundle, borrow or distribute the publisher's token or authenticated session. If an existing session's ownership is uncertain, have the user verify it locally before billable work. A valid existing user-owned login satisfies this requirement; do not ask the user to paste tokens into chat. Saved-export analysis needs no token.
