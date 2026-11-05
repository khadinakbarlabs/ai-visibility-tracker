# Automatic dashboard and charts

Generate this after **every** measurement or catch-up, without being asked. Charts come from real evidence only; with no measured data yet, show setup/coverage cards instead of empty charts.

## Where it appears

1. **In chat**, using the host's native visual tool when available (Claude artifacts or inline visuals, ChatGPT charts/canvas, Codex rendered files). Lead with the KPI row and the two most informative charts.
2. **Saved** in the project folder as `reports/<UTC timestamp>/dashboard.html` (self-contained), `report.md` (same content as text) and `metrics.csv` (the numbers behind each chart). Update `reports/latest.md` to point at it. Hosts without file storage offer the HTML as a download.

## Charts, in this order

| # | Chart | Data | Shown when |
| --- | --- | --- | --- |
| 1 | **KPI cards**: AI citation rate, change vs last matched run (pp), questions cited/observed, top competitor, spend this cycle, next run | Latest run + ledger | Always after a measurement |
| 2 | **Citation rate by platform** (horizontal bars, % with n) | Observed real checks per platform | Always |
| 3 | **Citation rate over time** (line per platform) | One point per matched-panel run | ≥2 comparable runs; gaps for missing runs, never zeros |
| 4 | **Question × platform grid**: Cited (rank) / Not cited / Unknown, as text in each cell plus color | Latest run tuples | Always |
| 5 | **Who AI cites instead** (bars: competing domain occurrences) | `competing_domains` deduplicated per check | Any competing citations |
| 6 | **Your cited pages** (table: page, times cited, platforms) | `cited_page_url` / `cited_pages` | Any citations |
| 7 | **Action tracker** (table: action, status, measured by question, result) | Action ledger | Always |
| 8 | Growth-scan panels: competitor traffic estimates, keyword demand, link prospects | Specialist outputs | Only when that module has evidence |

Every chart states its unit, date range, denominator (n observed checks) and panel revision. Unknown is a separate grey "Unknown" value, never 0%. Never join unlike panels on one line; start a new series at a panel change and label it.

## HTML rules

Self-contained static file: inline CSS and inline SVG charts, **no JavaScript, no remote scripts, fonts or images**. Escape all scraped text (`& < > " '`) before inserting it. Use CSS variables with a `prefers-color-scheme: dark` override, text labels on every bar/cell (color is never the only signal), `<table>` fallbacks with `<caption>`, and a single-column layout under 640px.

SVG recipes: bar width = `rate × chartWidth`; line points `x = runIndex × step`, `y = height − rate × height`; omit a point (break the path) for a missing run. Round rates to whole percents and show `cited/observed`.

Minimal skeleton (fill from real data; placeholders are not results):

```html
<!doctype html><html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>AI Visibility — {{PROJECT}}</title>
<style>
:root{--bg:#fbfaf7;--ink:#1c1b19;--muted:#6b675f;--card:#fff;--line:#e4e0d8;
--cited:#1f7a4d;--miss:#b4462f;--unk:#9a968d;--accent:#2f4f9e}
@media (prefers-color-scheme:dark){:root{--bg:#141412;--ink:#ecebe6;--muted:#a19d94;
--card:#1e1d1a;--line:#34322d;--cited:#4fbf87;--miss:#e0775f;--unk:#7d796f;--accent:#8ea8ef}}
body{margin:0;background:var(--bg);color:var(--ink);font:15px/1.5 system-ui,sans-serif}
main{max-width:1040px;margin:0 auto;padding:24px 16px}
.kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px}
.card{background:var(--card);border:1px solid var(--line);border-radius:10px;padding:14px}
.kpi b{display:block;font-size:28px} .muted{color:var(--muted);font-size:13px}
table{width:100%;border-collapse:collapse} td,th{padding:6px 8px;border-bottom:1px solid var(--line);text-align:left}
.c{color:var(--cited)} .n{color:var(--miss)} .u{color:var(--unk)}
</style></head><body><main>
<h1>{{PROJECT}} — AI search visibility</h1>
<p class="muted">{{DATE}} · panel {{PANEL}} r{{REV}} · {{OBSERVED}} of {{PLANNED}} checks observed</p>
<section class="kpis">{{KPI_CARDS}}</section>
<section class="card"><h2>Citation rate by platform</h2>{{SVG_PLATFORM_BARS}}</section>
<section class="card"><h2>Over time</h2>{{SVG_TREND_OR_NOTE}}</section>
<section class="card"><h2>Questions × platforms</h2>{{GRID_TABLE}}</section>
<section class="card"><h2>Who AI cites instead</h2>{{SVG_COMPETITOR_BARS}}</section>
<section class="card"><h2>Next actions</h2>{{ACTION_TABLE}}</section>
</main></body></html>
```

Keep dashboards private unless the user asks to publish or share them.
