# Use the user's available Apify access

The package remains skills-only and registers no MCP server, connector or runtime. The host LLM uses integrations already available to the user. Prefer an existing user-owned connection that can fulfill the task safely; keep the official CLI as the documented Postiz-style fallback. Never reuse the publisher's credentials.

| Route | Capability check | Credentials |
| --- | --- | --- |
| Connected Apify MCP/connector | Discover actual available tools and their schemas; check exact Actor identity, input, supported run options, status, storage, pagination and charges | Reuse the user's authorized connection; no extra key request |
| Official Apify CLI | Verify `apify api`/stdin/parameters and local login with suppressed account output | User's official local `apify login` |
| Existing authenticated API integration | Host must make secure HTTPS requests, inject secrets without exposing values, and support the documented API | User enters their own Apify API key in the host's secure credential setup |
| No usable access | Continue public research or analyze saved exports | Ask to connect Apify or complete secure key/login setup; never paste a key into chat |

## One-time connection

Apify access is the only account setup this plugin needs, and it runs **alongside onboarding, not before it**. Detect an existing route first and say nothing about setup when one works. Otherwise the assistant starts the sign-in itself, so the user only signs in to Apify in their browser — no copying keys:

| Host | What the assistant does |
| --- | --- |
| Claude Code, Codex or another host with a shell | Install the official CLI if missing, then run `apify login --method console` in the background. It opens Apify sign-in in the browser and hands the credentials back to the CLI automatically. Details: [CLI workflow](../../ai-visibility-tracker/references/cli-workflow.md#availability-and-authentication). |
| Claude (web, desktop, Cowork), ChatGPT or another connector host | If the host offers a tool to suggest or add connectors, use it to show the **Apify** connector so the user can sign in with one click (OAuth). Otherwise give one line: "Add the Apify connector (Settings → Connectors, server `https://mcp.apify.com`) and sign in with Apify." |
| Host with a secure secret/env setting only | Last resort: "Save your Apify API token as `APIFY_TOKEN` in this app's secure settings" (token from https://console.apify.com/settings/integrations). Use only if the host injects it without exposing the value. |

While the user signs in, continue researching the brand and preparing the plan; never block onboarding on it. Then verify silently with a read-only call (Actor metadata or account limits) and continue. A free Apify account works; its monthly credits bound what tracking can run (see [credits](credits-and-billing.md)). If the user pastes a token into chat anyway, do not repeat, store or use it; ask them to put it into the secure route above, and suggest rotating it in the Apify Console since chat history may retain it.

For MCP, inspect exposed tool schemas instead of inventing names or flags. The documented `call-actor` response provides status/storage IDs; retrieve actual dataset pages separately. Actor availability and permissions vary. Prefer a route that applies the authorized `maxTotalChargeUsd` as a run option, not Actor input, and retrieves required provenance. If a connector cannot set a charge cap, it may still run a mapped pay-per-event Actor when the validated input fixes the number of billable events (for example an exact keyword × question × platform panel) and the worst case — events × current event price + startup charges — fits the run's allocation; record the cap as `input-bounded` in the ledger. Otherwise use another verified route or explain the missing setup before paid execution. Never silently remove caps to use an easier tool. Do not run paid browser/discovery Actors outside the approved plan.

For direct API access, use only `https://api.apify.com` with the documented `/v2/actors/...`, same-task run/storage endpoints and separately approved schedule endpoints. Use structured JSON and numeric query parameters; the start request is `POST /v2/actors/ACTOR_ID/runs` with Actor input as JSON body and run controls such as `maxTotalChargeUsd`, `timeout` and `build` as documented parameters. Secret injection belongs to the host's credential mechanism using an Authorization header; never place tokens in URLs, commands, tool-visible arguments, files or reports. If the host cannot inject a secret safely, require CLI login or a supported connection. Do not read auth files or echo environment secrets.

Apply [execution](execution.md) identically across routes: mapped Actors, current schema/pricing, shared reservations, no duplicate starts, same-run evidence, pagination, real coverage and charge reconciliation. Switching route does not authorize another run or reset the ledger. Keep a non-secret route/capability label in state. Authenticate only to the user's account; uncertain ownership requires local verification. No installation or host configuration mutation is implied by capability discovery.

Sources verified 2026-10-03: [Apify MCP](https://docs.apify.com/integrations/mcp), [API authentication](https://docs.apify.com/api/v2), [Run Actor](https://docs.apify.com/api/v2/actors-runs-post). Refresh official documentation and exposed schemas when using a connection.
