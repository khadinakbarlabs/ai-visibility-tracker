# Official Apify CLI workflow

This is the Postiz-style dependency boundary: the plugin ships skills; the independently installed CLI authenticates and executes. Use `apify-cli`, published by Apify, not a custom or invented visibility CLI. Commands and stdin/parameter flags were verified with local CLI 1.8.0 and current official docs on 2026-10-03.

## Availability and authentication

```sh
apify --version
apify api --help
jq --version
apify info > /dev/null
```

The last command verifies the local logged-in account without printing account details. On an auth failure, the user completes `apify login` in their own terminal. Never run `apify auth token`, inspect auth files or ask for API keys in chat. Existing CLI authentication is sufficient; do not force reauthentication when a read succeeds.

If the CLI is absent, explain the external dependency and use the user's installation policy. The supported npm installation is `npm install -g apify-cli`; Node/npm or an official platform-specific installer is needed. Install/upgrade only that dependency within the user's authorized setup scope. Do not install MCP servers or alter unrelated host settings. If `apify api --help` lacks `--body` or `--params`, update via the official CLI release path or give the user a setup requirement; do not invent flags.

## Inspect the fixed Actor

```sh
apify api GET /v2/actors/CFYLF6fOcyvdofuof/builds/default/openapi.json \
  | jq '.components.schemas.inputSchema'
apify api GET /v2/actors/CFYLF6fOcyvdofuof \
  | jq '.data | {id, name, username, pricingInfos}'
```

Select the effective pricing entry with the latest `startedAt` that is not in the future. The billed check event is `keyword-visibility-checked`. Calculate event estimate from its `eventPriceUsd` and the planned check count. Inspect startup events and `isPPEPlatformUsagePaidByUser`; do not turn an absent field into a claim of free platform usage. Only these selected public metadata fields belong in the report. The convenience `actors info --input --json` command can return broad metadata in the verified CLI; use the narrow API schema command instead.

## Start with a budget

Write `input.json` in a private user-selected work directory. Replace the example charge cap with the amount already authorized by the user. The cap is an API query parameter, separate from Actor input:

```sh
apify api POST /v2/actors/CFYLF6fOcyvdofuof/runs \
  --body - \
  --params '{"maxTotalChargeUsd":2,"timeout":600,"build":"latest"}' \
  < input.json
```

It returns an API envelope with `.data.id` and initial run status. Save that ID immediately. This is a billable action; the example `$2` is not implicit spend authorization or a guarantee that platform/account costs are included. Respect the host's permission flow. A successful POST is submission evidence, not completed result evidence. Do not automatically retry a failed or timed-out POST: it may already have created a run.

Keep user prompts in the JSON file rather than interpolating them into shell commands. Treat run/storage IDs as alphanumeric identifiers returned by Apify, not executable strings. Quote filenames with spaces. Restrict this workflow's API calls to the named Actor and the run/storage identifiers it returns; arbitrary API mutation is outside the workflow.

## Status and resumption

```sh
apify runs info RUN_ID --json
apify runs ls CFYLF6fOcyvdofuof --desc --limit 10 --json
```

Substitute the actual returned ID. The list command is for recovering an uncertain submission; do not publish unrelated runs in the user's report. Match input/start time before deciding whether a fresh run is needed. Poll status with bounded reads at roughly 15–30-second intervals, retain the run ID and keep the user informed. `apify runs wait` can block; interrupted waiting is not permission to relaunch.

Verify `actId: CFYLF6fOcyvdofuof`. Terminal statuses include `SUCCEEDED`, `FAILED`, `ABORTED`, `TIMED-OUT`. Preserve `buildId`, start/end timestamps, `usageTotalUsd` and charged event counts if returned. Charges are observations, not estimates; state when charge fields are unavailable or still settling.

## Collect only this run

Get the IDs from its run metadata. In a private directory, read:

```sh
apify key-value-stores get-value STORE_ID INPUT
apify datasets get-items DATASET_ID --format json --limit 100 --offset 0
apify key-value-stores get-value STORE_ID LAST_RUN_SUMMARY
```

Continue dataset pages at offsets 100, 200 and so on until a short/empty page; do not treat the first page as the full dataset. Check `OUTPUT` and `RUN_SUMMARY` too if those records exist. A missing optional summary record is acceptable only after confirming not-found; auth, quota or server errors must be reported and resolved. Collect failed runs too when useful, but identify incomplete coverage.

Save input, rows, summary and selected run metadata outside the plugin using private permissions and distinct names. In POSIX shells, use `umask 077` and `set -C` before redirection to prevent accidental public permissions and overwriting; on other hosts use equivalent private-file and no-overwrite controls. Check command exit status before reading a redirected file as evidence. Never package user results, auth material or raw logs into a plugin release.

Use local JSON analysis tools already available to the host for formulas in the Actor contract. This plugin does not include an executable analytics script. Read-only analysis of saved exports requires neither a new Actor run nor a fresh API token.

## Errors

| Condition | Action |
| --- | --- |
| CLI missing / incompatible flags | Set up the official CLI within the user's authorized scope. |
| Auth or authorization error | Have the user complete local login/check Actor access; keep tokens out of chat. |
| Quota/rate limit | Respect the limit and use a delayed read; do not expand paid run scope. |
| Ambiguous submission | Recover recent matching runs before any resubmission. |
| Successful run with diagnostics only | Report a health check or invalid-input result; no visibility metrics. |
| Partial provider failure or charge cap | Report observed checks and missing tuples separately. |
| No sources in an answer | Distinguish no-source evidence from a competitive content gap. |
| Host lacks execution/network | Provide commands or analyze a supplied export; no simulated live result. |

Sources: [official CLI commands](https://docs.apify.com/cli/docs/reference), [Run Actor API](https://docs.apify.com/api/v2/actors-runs-post), [Postiz CLI skill pattern](https://github.com/gitroomhq/postiz-agent/blob/main/skills/postiz/SKILL.md). The Postiz repository also contains other integrations; this plugin adopts only its skill-to-external-CLI pattern.
