# Apify credits: check before spending, stop cleanly when out

All paid work runs on the user's own Apify account and credits. The assistant checks credits itself; the user only hears about billing when action is needed.

## Before every paid launch

Read the account's usage limits through the connected route: `GET https://api.apify.com/v2/users/me/limits` (CLI: `apify api GET /v2/users/me/limits`; connector: its equivalent account/limits tool when exposed). Use only these fields:

- `limits.maxMonthlyUsageUsd` — the account's monthly usage limit.
- `current.monthlyUsageUsd` — usage so far this cycle.
- `monthlyUsageCycle.endAt` — when the cycle resets (show it in the user's timezone).

`remaining = maxMonthlyUsageUsd − monthlyUsageUsd`. Compare it with this run's cap plus held reservations. Save `{checkedAt, remainingUsd, cycleEndAt}` on the project; never save account identity, plan details beyond these numbers, or tokens.

| Result | Action |
| --- | --- |
| Remaining covers the run | Launch silently. |
| Remaining after this run would fall below 20% of the limit | Launch, then add one line to the report: "Apify credits are running low: about $X left until DATE." Warn once per cycle. |
| Remaining is below the run cap | Do not launch. Pause the project (below). |
| Limits endpoint unavailable to this route/token | Continue with per-run caps; rely on the run-failure handling below. Do not ask the user to change token permissions just for this. |

The monthly cap in the project's standing approval is separate: if the next run would exceed it, pause the same way and offer to raise the cap.

## When a run fails for credits

Treat these as **out of credits**, not as a research failure: HTTP 402, a run or start error mentioning usage limit, "Monthly usage hard limit exceeded", insufficient credits or a platform usage cap. Do not retry. Keep any rows already collected as partial evidence.

## Pausing for credits

1. Set the project status to `paused_credits` with the date and reason.
2. Disable only this project's own recurring jobs (matched by their recorded IDs/ownership marker) so they stop failing. Never touch other schedules or change account-wide limits.
3. Keep all history, the plan and the standing approval.

## The message to the user (once, short)

> Your Apify credits for this cycle are used up (about $USED of $LIMIT). I've paused tracking for **PROJECT**, so nothing more will be charged.
>
> To keep tracking, either:
> - **Upgrade your Apify plan** for more monthly credits: https://apify.com/pricing (manage it in Apify Console → Billing), or
> - **Raise your usage limit / add credits** on a paid plan in Apify Console → Billing → Limits.
>
> Your credits also reset on **DATE**. Say **"resume tracking"** when you're ready, and I'll pick up where we left off.

Do not repeat the message on every scheduled occurrence; one notice per pause. Offer the cheaper alternative in the same message only when useful ("or switch to weekly to stay within free credits").

## Resuming

On "resume tracking", on the next user visit, or at the next recurring agent execution: re-check limits. When the remaining credits cover the next run, re-enable this project's jobs, verify them by readback, set status back to tracking, and continue the normal loop, including catch-up of any runs that did complete. Resuming within the original plan and caps needs no new approval. If credits are still short, stay paused quietly.
