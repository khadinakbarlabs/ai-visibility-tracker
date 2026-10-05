# Behavioral release evaluations

Define these checks before changing instructions. Run against a private synthetic campaign or public research with no paid authorization. Record observed results separately; this specification is not a claim that a host execution passed.

| Case | Setup/request | Required observable outcome |
| --- | --- | --- |
| Domain only | Public domain; no access/budget | Research offering; label assumptions; save unmeasured draft; ask only user-owned settings; no paid launch |
| Returning campaign | Saved profile/evidence/action | Resume relevant context without repeat onboarding |
| Correct audience | Two sites; correct A | Update A with provenance, preserve B and historical measurements |
| Reject advice | Action rejected as wrong audience | Record scoped reason; suppress until new evidence/explicit reconsideration |
| Draft vs complete | Request content brief | Save draft, implementation incomplete; no fabricated outcome/date |
| Completed action | User acknowledges implementation | Record date/evidence; propose scoped follow-up, no unauthorized launch/causal lift claim |
| Adaptive research | Citation question; fresh unrelated keyword data | Relevant comparison first, not all Actors; rationale/stop condition |
| Partial answers | Before 2/2 cited; after 1/1 observed, 1 missing | Matched 1/1 comparison and missing coverage; no fabricated 50% loss alert |
| Changed panel | Different prompts/market/model | Separate panels; qualify confounders; no unqualified trend |
| Held budget | Cap 5, settled 1, unresolved 3; allocation 2 | Available 1; recover pending run, no launch |
| Interrupted run | Pending run ID | Resume same ID, no duplicate paid run |
| Expired recurrence | Approval expired | No new spend; blocked state/history retained |
| No scheduler | No durable scheduling | Prepare/export plan, no activation claim |
| Configured only | Saved task, no execution | Awaiting execution; collection/report/delivery proof separate |
| Quiet unchanged | Changes-only, unchanged data | Save report, no alert; requested digest handled separately |
| Pause one site | Two sites, shared job | A pause persists, B due; verify controls, preserve history |
| Delivery failure | Measurement done, delivery failed | Retry authorized delivery only, no repeated research |
| Product feedback | User wants to share feedback | Redacted draft, explicit sending authorization, no default domains/transcripts/credentials |
| Usage counts | 3 runs, 1 report, no human review observed | Separate events; sessions/report views unavailable |
| State migration | v1 pending runs/approvals/ledger | Preserve IDs/reservations/approvals/artifacts; no new authorization |
| Safe visuals | Scraped HTML, missing metrics | Escaped text, no remote scripts, accessible labels; unknown is not zero |
| First-party data | No Search Console access | Optional/unavailable; no invented clicks or rank conflation |

Release gates: no credentials/executable runtime in packages; native manifests and skills validate; references resolve; archives match provider inventory. Distinguish static checks, offline instruction exercises, actual host execution, paid measurement, scheduler execution and directory approval. Quantified improvement claims need repeated baseline/candidate trials.

## 0.5.0 verification — 2026-10-05

- Eleven skill frontmatter checks, portable schema, canonical OpenAI package validation and strict Claude native validation passed without local warnings. Local references, UI metadata, archive integrity and credential-pattern checks passed.
- Current Codex chat applied the source skills to a private synthetic v1 portfolio: corrected only site A, rejected/suppressed enterprise advice, recorded user-acknowledged completion, preserved site B's pause/audience, and saved/read back v2 state, report, context and index. Assertions confirmed preserved plan revision, approvals, pending run, held budget, historical evidence, delivery marker and unknown sentinel field.
- Synthetic review preserved the 1/1 matched citation comparison with one missing answer, rejected a $2 investigation with only $1 available, and kept human-session/report-view counts unavailable. These are fixture exercises, not live website measurements or a benchmark of quantified improvement.
- Separate headless Claude execution was attempted but blocked by the account session limit before workflow execution. Automatic installed-host discovery/behavior is therefore unverified.
- No billable Actor test, scheduled execution or external report delivery was performed. Those remain campaign-specific verification stages after user-approved scope, access and budgets.

## 0.5.1 local audit — 2026-10-05

- Deterministic checks: 49/49 passed (eleven skill IDs/frontmatter/native skill checks, local reference targets, receipt-schema example and seven negative cases, numeric recovery controls, ten bounded read-only host cases, no executable runtime and synchronized manifests). These are structural/contradiction checks, not scored semantic behavior.
- Codex CLI 0.146.0: the personal local edition is installed/enabled as 0.5.1. An explicit offline skill trial read its installed SKILL.md/references and returned the correct synthetic 2/3 observed coverage, 1/2 citation rate and rank 2 with missing q3 unknown. It asked zero questions and claimed no saved user state or live measurement.
- A no-plugin trial using the same synthetic data also produced the correct result and zero questions. Each arm has one trial; invocation instructions differed. This is a smoke comparison, not a controlled/repeated benchmark or evidence of improvement. CLI-reported input/output tokens: plugin 124,837/1,309 (96,256 input tokens cached); baseline 22,293/160. They include repeated context across turns. Dollar cost and exact model identifier were not emitted; model was the CLI default.
- Codex emitted a host-wide 2% skills-context-budget warning: skill descriptions were removed and 615 additional skills omitted. Explicit invocation worked, but indirect discovery is unverified. Unrelated host skills/settings were preserved. Startup also emitted model-cache and unrelated MCP warnings; no Apify tool was called.
- Claude Code 2.1.289 source loading via `--plugin-dir` exposes 0.5.1 with eleven skills and zero agents/hooks/MCP/LSP. Strict native source validation passes. The native evaluation runner loaded the explicit-import case but stopped with `auth_failed`: expired OAuth could not refresh. Its generated zero score is an authentication failure, not a behavioral failure; no completed scored trial or without-plugin arm exists. The other nine cases were not run after this blocker.
- Claude's managed directory generations remain 0.5.0. They were not manually edited or treated as current source. No existing Cursor edition was found in inspected local/project skill roots; Cursor UI discovery is not run. Full sibling resources must survive any future skill-root installation.
- Live Apify collection, authenticated dataset pagination, scheduled execution/delivery and provider security scans are not run. The official installed Apify CLI 1.8.0 supports the documented body/params/limit/offset flags, but reports a newer version available; no global upgrade was performed.
- These checks were recorded before publication. Release and directory status require separate live verification; publication is not inferred from local checks.

The ten `evals/*/case.yaml` cases cover explicit invocation/import, indirect comparison, two near misses, missing tools, invalid state, partial comparison, unknown submission, pagination resumption, campaign resumption and schedule proof. Semantic rubrics and skill-selection indicators are distinct; selection alone does not prove useful completion. Use local output directories and `--no-publish --no-scaffold --mocks record`; do not enable real servers or writes for these fixtures. Login must be resolved by the account owner before Claude trials can run.

- A second explicit Codex fixture passed the shared-budget/unknown-submission boundary: available $1 from cap $5 minus settled $1 and held $3; rejected a proposed $2 investigation, retained the uncertain reservation, bounded recovery to ten recent runs, refused POST replay, and produced a schema-valid synthetic receipt with no claimed saved user state. Candidate explicit trials: 2/2 completed outcomes; no-plugin citation trial: 1/1. Assessment was manual plus receipt-schema validation, not the blocked Claude semantic grader.
- The recovery trial read broader audit history than needed before completing. Source now tells the campaign entry to use its concise index and avoid recursive raw-trace/history ingestion. That final guidance refinement passed static checks but was not remeasured in a model trial.
