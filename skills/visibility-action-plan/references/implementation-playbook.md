# Recommendations with implementation steps

Every recommendation must be something the user (or the assistant, with permission) can implement today. Each one has: **what to do, where, exactly how, effort, and how the next run will measure it.** Lead with at most three. Pick recipes from the evidence pattern; never apply the whole list.

## Action format

```markdown
### 1. [Short imperative title] — [effort: 30 min | half day | 1–2 days] · [priority: high/med/low]
**Why:** [observation with numbers, platform, question, date, competing source]
**Where:** [exact URL or "new page at /suggested-path"]
**Do this:**
1. [concrete step]
2. [concrete step]
**Ready-to-use:** [copy block, schema snippet, outline or robots rule, when relevant]
**We'll measure it by:** [tracked question(s) × platform(s)] on [next run date]
```

Save each action with ID, evidence links, target URL, status (proposed → accepted → in progress → completed / deferred / rejected), measured-by tuples and follow-up date. On later runs, report the measured result beside the action; a change after implementation is an observation, not proof of cause.

## Recipes by evidence pattern

| Evidence pattern | Recommended implementation |
| --- | --- |
| Not cited; competitors cited for a question; no matching page on the site | **Create an answer page** for that question (outline below). |
| Not cited; a relevant page exists | **Upgrade the page**: direct answer first, add the missing sub-questions, a comparison table, sourced stats, visible author + updated date. |
| Cited on some platforms, not others | Check crawler access for the missing platform (robots table below), then make the page's answer block more self-contained. |
| AI cites third-party sources (review sites, listicles, forums, directories) instead of brands | **Get onto those sources**: list the exact URLs from the run; recommend legitimate listing, review requests from real customers, or a useful contribution. Hand prospects to `link-opportunities`. |
| Your cited page is a weak or outdated one | Point internal links and the answer block to the best page; refresh the cited page. |
| Brand questions answered without your site | **Entity clarity**: About page facts, `Organization` schema with `sameAs` profiles, consistent name/description across profiles. |
| Content gap rate high across many questions | Plan a small topic cluster: one pillar page + 3–5 answer pages linked together. |
| Keyword demand high, no AI/Google presence (growth scan) | Add the term to the panel and create/upgrade the matching page. |

### Answer page outline

1. H1 = the question in the user's words.
2. A 40–60 word direct answer immediately below (definition, recommendation or steps).
3. H2 sections for the 3–5 follow-up questions seen in AI answers and competitor pages.
4. A comparison table or step list where the topic allows.
5. Specific facts with sources and dates; your own data or examples when available.
6. Author, last-updated date, internal links to product/pricing pages.

### Structured data (adapt; validate with Google's Rich Results Test)

```html
<script type="application/ld+json">
{"@context":"https://schema.org","@type":"Article",
 "headline":"[Question as headline]","dateModified":"[YYYY-MM-DD]",
 "author":{"@type":"Person","name":"[Author]"},
 "publisher":{"@type":"Organization","name":"[Brand]","url":"https://[domain]",
   "sameAs":["https://www.linkedin.com/company/[brand]","https://x.com/[brand]"]}}
</script>
```

Add `FAQPage` only for real on-page Q&A. Schema helps machines understand the page; it does not guarantee citations.

### AI crawler access (check `https://[domain]/robots.txt`)

| Platform | User agents to allow for search/answers |
| --- | --- |
| ChatGPT | `OAI-SearchBot`, `ChatGPT-User` (`GPTBot` is training; allowing it is the user's choice) |
| Perplexity | `PerplexityBot`, `Perplexity-User` |
| Claude | `Claude-SearchBot`, `Claude-User` (`ClaudeBot` is training) |
| Gemini / Google AI | `Googlebot` for Search features; `Google-Extended` controls Gemini use, not Search inclusion |
| Copilot | `Bingbot` |

Only recommend a robots change when the file actually blocks a relevant agent; quote the blocking line. Also flag pages that need JavaScript to show their main text, `noindex`, or login walls. `llms.txt` is optional and ignored by Google; never present it as a fix by itself.

## "Implement it for me"

When the host can access the user's site source or CMS (for example a repository open in Claude Code or Codex), offer to apply an accepted action: show the exact diff or page draft, apply it only after the user says yes, and never commit, push, deploy or publish without explicit permission. Without access, deliver copy-paste-ready content and a short checklist. Mark the action **in progress** when drafted and **completed** only when the user confirms it is live or a later fetch of the live page shows it.

## Never

Promise rankings or citations, recommend buying links or fake reviews, invent statistics, or re-recommend a rejected action without new evidence.
