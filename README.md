# AI Search Visibility Tracker

A **skills-only plugin** that uses your available Apify connection or the separately installed official **Apify CLI**, retaining Postiz's skill-to-CLI fallback. Its citation workflow runs [Khadin Akbar's AI Search Visibility Tracker](https://apify.com/khadinakbar/ai-search-visibility-tracker) to measure domain/page citations, citation position, content gaps and competing domains in AI search answers.

Eleven coordinated skills support guided onboarding, one or multiple websites, AI SEO, answer engine optimization (AEO), generative engine optimization (GEO), AI citation baselines and comparisons, competitor traffic and Google rankings, keyword opportunities, search trends, backlink samples, link prospects, scheduled tracking and reports. The package includes no executable scripts, server, MCP connection, hooks, npm package or bundled dependencies.

Version 0.5.0 adds goal-driven research, private business context and corrections, action/feedback history, returning reviews, concrete briefs and accessible saved report templates. The host selects useful checks within your approved scope instead of running every Actor automatically. These instructions depend on the host's available research, storage, visualization and scheduling capabilities.

## Requirements

Use your own authenticated Apify account through a capable existing MCP/connector, secure API integration or official CLI. The CLI fallback requires host shell/network access and JSON tools such as `jq`. Apify charges apply. No separate AI-provider keys are supplied by this plugin. A chat surface can execute through a capable connected Apify tool even without a shell. Without any usable connection it can research public pages, analyze exports and prepare a plan.

If needed, install the official CLI with `npm install -g apify-cli`, then complete `apify login` in your own terminal. Keep your API token in Apify's local authentication flow; do not paste it into chat or package files. Verify with `apify info > /dev/null`.

## Use

Start with `$seo-growth-agent` on OpenAI/Codex or `/ai-visibility-tracker:seo-growth-agent` on Claude Code for the complete campaign. It routes first use through guided onboarding and resumes saved settings on return. Specialist skills are roles guided by the host, not separate bundled processes.

### Guided onboarding

Give the assistant a website and goal. Your host's LLM researches the public offering, audience signals, competitors, topics, keywords and AI questions, then proposes useful market/device and tracking defaults. It asks only for missing information on your side: account access, spending limits or consequential private preferences. Sources, assumptions and unmeasured metrics stay visible. Existing access and approvals are reused; paid work and recurring activation require authorization to the concrete plan.

Each website can have multiple markets and panels with its own competitors, settings, allocation, results and schedule status. All websites share one portfolio budget. Saved profiles, measurements and ledgers live in your private chosen directory outside the plugin; no public signup or publisher account is used. Add or pause a website without discarding other sites or past baselines.

### Visual reports and future context

Results include a readable dashboard, keyword table, AI question/platform matrix, competitor comparisons and evidence-linked actions where data exists. Comparable results can include charts; missing measurements remain unknown. Reports, JSON/CSV observations, source/run evidence and concise context are saved privately outside the package and resumed on return. Hosts without persistent storage provide downloadable state rather than claiming automatic memory. See [reporting](skills/seo-growth-agent/references/reporting.md).

Reports lead with what changed, why it matters, the next three actions and the next approved check. The work queue distinguishes drafts from acknowledged implementation and retains feedback and follow-up evidence. Existing schema-v1 campaigns migrate with a private backup, preserving pending run IDs, approvals, budgets, pauses and history. No dashboard service or guaranteed cross-host interactive controls are bundled.

### Useful reviews and private feedback

Ask “What changed?”, “What should I do this week?”, “Make a brief for this action”, “I completed this”, “Correct the audience for this website” or “Show what you know about my business.” Feedback can mark work useful, already done, wrong audience, too much effort or incorrect. It guides future recommendations and avoids repeating rejected work; it doesn't train the underlying model.

Context is separate per website/market, with evidence dates and labelled assumptions. You can inspect, correct and export it or request removal using available host controls. Optional existing authorized Search Console tools or analytics exports can inform priorities; no Google integration or access scopes are included. First-party average position remains separate from sampled SERP rank.

The plugin sends no publisher telemetry. Observable local user reviews, runs, report generation and delivery are separate events; background jobs don't count as human sessions. Product feedback is an optional redacted draft shared only with your authorization. See [feedback and review procedures](skills/seo-growth-agent/references/feedback-and-reviews.md).

### Scheduled tracking and reports

Use `$scheduled-visibility-tracking` or `/ai-visibility-tracker:scheduled-visibility-tracking` to configure, inspect, change, pause or resume approved tracking. A host with verified recurring agent execution can run due research modules, reconcile budgets, compare matching panels and produce per-site reports, portfolio rollups and authorized alerts. Execution, state access, credentials and delivery must work in that scheduler's environment.

Alternatively, Apify cloud schedules run fixed-input measurements while the chat is closed. They collect data; report analysis is on demand unless a separate host report job is verified. Their per-action charge caps do not enforce a shared monthly portfolio maximum or automatic end date. A hard monthly cap or expiry requires a verified controller before activation. The setup flow explains capabilities and costs, avoids duplicate runs and verifies saved schedules and actual executions. Installing the plugin alone activates nothing. See [scheduler procedures](skills/scheduled-visibility-tracking/references/scheduling.md).

OpenAI/Codex: invoke `$ai-visibility-tracker`, `$visibility-trends` or `$visibility-action-plan`, or describe your goal naturally.

Claude Code: invoke `/ai-visibility-tracker:ai-visibility-tracker`, `/ai-visibility-tracker:visibility-trends` or `/ai-visibility-tracker:visibility-action-plan`. To test a source folder without installing, launch `claude --plugin-dir /path/to/ai-visibility-tracker`.

Examples:

- “Check whether ChatGPT, Perplexity and Gemini cite ahrefs.com for backlink research. Use these two exact buyer questions, with a $2 run budget.”
- “Compare these two saved citation checks and show which page citations were gained or lost.”
- “Create a content plan for topics where competing domains were cited and my site was absent.”
- “Onboard my three websites, propose weekly citation checks and monthly competitor/backlink research, and show one portfolio budget before activating anything.”
- “Pause tracking for the second website and keep the other sites running.”

The main skill prepares input and checks current pricing before a billable run. Exact questions use `queryTemplates: []`; this Actor repeats them unchanged for each keyword. See the [Actor contract](skills/ai-visibility-tracker/references/actor-contract.md) and [CLI workflow](skills/ai-visibility-tracker/references/cli-workflow.md).

## Specialist workflows

| Skill | Purpose |
| --- | --- |
| seo-growth-agent | Adaptive research, shared budget, saved context, returning reviews and feedback |
| visibility-onboarding | Guided intake, website/market settings and plan review |
| scheduled-visibility-tracking | Recurring setup, verification, pause/resume and reporting |
| ai-visibility-tracker | AI domain and page citation baseline |
| visibility-trends | Compare matching saved AI citation panels |
| competitor-intelligence | Competitor discovery, traffic estimates and Google ranks |
| keyword-opportunities | Keyword ideas, search demand and available difficulty |
| search-trends | Seasonality and relative search interest |
| competitor-backlinks | Compare capped backlink samples |
| link-opportunities | Qualify prospects using backlinks and AI citation sources |
| visibility-action-plan | Combine evidence into one prioritized action queue |

Read the [mapped Actor contracts](skills/seo-growth-agent/references/actor-contracts.md) and [campaign execution rules](skills/seo-growth-agent/references/execution.md). Live specialist research uses seven additional mapped Apify Actors through a verified user-owned route. Examples do not authorize spending; the campaign shares one total cap. Traffic is estimated, Trends are normalized, and backlink samples are incomplete. Results cannot guarantee improved ranks or AI citations. AI content detection is outside this release.

## Open-source repository

This repository is the single source for all eleven skills, platform manifests, artwork, support and policy documentation. Plugin files are MIT licensed. Use GitHub issues for redacted bug reports and pull requests for improvements. Never include API tokens, authentication files or private research exports.

## Distribution

The OpenAI export contains the portable root manifest and a synchronized Codex compatibility manifest. The Anthropic export contains only its native `.claude-plugin/plugin.json` manifest. Both include the same skills and references; only the OpenAI export includes `agents/openai.yaml` UI metadata. Archives isolate the provider-specific files.

Host installation does not create paid runs or schedules. A verified local package is distinct from public directory approval. Public listings require real publisher, policy/support URLs, permitted availability and platform review; missing declarations are not fabricated.

Release behavior checks are specified in [EVALUATIONS.md](EVALUATIONS.md). Package validation, actual host behavior, billable Actor results, scheduled delivery and platform review are separate verification stages. No quantified intelligence or ranking improvement is promised.

## Data and limits

Topics, domain and optional page/competitor targets are sent through your selected connection to Apify for the requested Actor. Credentials remain managed by the CLI or host's secure authentication mechanism. Results and run records live in your Apify account; local exports belong in a private directory outside this package. Do not submit personal, confidential or customer data as AI search prompts.

Citation measurements are sampled API observations, not universal rankings across consumer apps. Missing/diagnostic results are unknown, citation position refers to the source list, and observed changes do not establish causation. No sentiment or brand-mention metrics are claimed for this Actor. Recurring tracking needs your approved cadence, spend, duration and reporting settings plus a configured and verified durable schedule. A host without any capable execution connection supports public research, planning and saved-export analysis.

## Product pages

Maintained by Khadin Akbar. See the [product website](https://github.com/khadinakbarlabs/ai-visibility-tracker), [support page](https://github.com/khadinakbarlabs/ai-visibility-tracker/blob/main/SUPPORT.md), [privacy notice](https://github.com/khadinakbarlabs/ai-visibility-tracker/blob/main/PRIVACY.md) and [terms of use](https://github.com/khadinakbarlabs/ai-visibility-tracker/blob/main/TERMS.md).

## User-owned credentials

Every live user authenticates to their own Apify account through an existing authorized connector/MCP connection, official local `apify login`, or secure host API-key setup. Never use, bundle, borrow or distribute publisher credentials. If ownership is uncertain, have the user verify the account locally before billable work. Existing user-owned access is sufficient; ask for connection or secure key setup only when access is missing. Never solicit tokens in ordinary chat or save them in campaign records. Saved-export analysis needs no token.

## License

Plugin files are available under the [MIT license](LICENSE). The license applies to this skills package; separately operated Apify Actors and third-party services retain their own terms. Users supply their own Apify account through authorized connection, local login or secure API-key setup.

## Research and discovery keywords

AI visibility, AI search, AI SEO, SEO, AEO (answer engine optimization), GEO (generative engine optimization), LLM search, ChatGPT citations, Perplexity citations, Gemini citations, citation tracking, competitor analysis, competitor intelligence, estimated website traffic, SERP analysis, Google rankings, keyword rank tracking, keyword research, keyword opportunities, search demand, keyword difficulty when available, Google Trends, search trends, seasonality, backlink analysis, backlink research, link building opportunities, link prospect research, content gaps, guided onboarding, multi-website tracking, scheduled tracking, portfolio reporting, Apify CLI, and agent skills.

These terms describe the supported research workflows; they do not promise universal visibility measurements, complete backlink coverage or ranking gains.
