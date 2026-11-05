# Release notes

## 0.6.1 — 2026-11-05

- Apify connection now happens on the side: the assistant installs the official CLI if needed and starts `apify login --method console`, which opens Apify sign-in in the browser and returns credentials to the CLI automatically. Connector hosts show the Apify connector's one-click sign-in when the host can suggest connectors.
- Onboarding no longer waits for sign-in; research and the plan proceed in parallel, and the baseline starts once access works.
- Manual token entry is a last-resort secure-settings fallback; tokens are still never pasted into chat or passed as command arguments.

## 0.6.0 — 2026-11-05

- **Autopilot by default.** Setup takes at most two user turns: connect Apify once (connector, `apify login` or secure `APIFY_TOKEN`) plus brand/website/must-track keywords, then one priced "How often should I track this?" choice — Weekly, Daily, Hourly pulse or On demand. That choice is the standing approval; no further per-run, per-keyword or per-chart questions.
- After the choice the assistant runs the baseline, generates the dashboard, writes recommendations with implementation steps, configures and verifies the schedule and saves project memory automatically.
- **Per-project memory** in `~/.ai-visibility-tracker/projects/<projectId>/` with a project index; projects are matched by brand, domain or workspace and never mixed.
- **Automatic dashboard** after every run: KPI cards, citation rate by platform, trend over time, question × platform grid, competing domains, cited pages and action tracker; self-contained static HTML (no JavaScript), Markdown and CSV.
- **Implementation playbook**: every action has exact page, numbered steps, ready-to-use outlines/schema/robots guidance, effort and the tracked questions that will measure it; optional "implement it for me" with explicit approval.
- **Credit handling**: checks Apify usage limits before each paid launch, warns once when credits run low, pauses only the project's own jobs when credits run out, sends one upgrade/add-credits message and resumes after credits return.
- Catch-up on return: fetch completed scheduled runs before launching anything new.
- Connector routes without a run-level charge cap may run fixed-panel pay-per-event inputs whose worst-case cost fits the allocation (`input-bounded`).
- Three new offline eval cases: autopilot-first-run, frequency-choice, credits-exhausted.

## 0.5.1 — 2026-10-05

- Route concrete imports, comparisons, repairs and resumes directly; keep account prerequisites beside live collection.
- Bound status reads, page downloads, retries and ambiguous-submission recovery; preserve partial checkpoints and held reservations.
- Add a private operation-receipt schema, safe error taxonomy and executable handoff instructions without bundling runtime.
- Add ten offline native host cases with semantic and selection graders; report blocked evaluations separately from passes.
- Preserve stable plugin/skill IDs, Actor mappings, shared budgets, user-owned credentials and recurrence gates.


## 0.5.0 — 2026-10-05

- Research-first onboarding and multiple websites/markets with one portfolio ledger.
- Goal-driven specialist selection, scoped business context, freshness and testable hypotheses.
- Private corrections, recommendation feedback, action statuses, useful briefs and follow-up plans.
- Returning reviews and accessible saved portfolio/website report templates.
- Capability-aware recurring tracking, requested digests, quiet alerts and separate execution/delivery proof.
- Backward-compatible campaign-state migration with preserved approvals, pending runs and budgets.
- Optional existing first-party data and user-reviewed redacted product feedback; no publisher telemetry.

Skills-only; each user supplies their own Apify access. Scheduling, durable storage and visual artifacts depend on host capabilities. Actor usage is billable. No guaranteed ranking gains, autonomous service or quantified intelligence improvement is claimed.
