---
name: Check market status before trading-hours logic
description: Determine whether the U.S. market is open or closed for a date or date range, and verify Market Data API service health before dispatching data jobs.
api: openapi/marketdata-app-markets-api-openapi.yml
operations: [getMarketStatus]
generated: '2026-07-22'
method: generated
---

# Check market status before trading-hours logic

## Auth

Send `Authorization: Bearer <token>`. The service-status endpoint requires no token.

## Steps

1. **Market open/closed** — `getMarketStatus`: `GET /markets/status/` with an optional `date`, `from`/`to` range, or the relative keyphrase `last session` (returns the previous closed session, accounting for weekends, holidays, and half-days). Response `status` is `open` or `closed`.
2. **Service health (no token)** — `GET https://api.marketdata.app/status/` returns per-service online status plus 30-day and 90-day uptime, updated every 5 minutes. Check it before retrying failed jobs so you do not hammer a service that is already down; the human-readable page is https://status.marketdata.app/.

## Rules

- Schedule daily jobs around the credit-window reset at 9:30 AM Eastern (NYSE opening bell); use the `America/New_York` timezone identifier, never a fixed UTC offset.
- Treat HTTP 203 as success; errors use `{"s": "error", "errmsg": "..."}`.
- 5xx responses (including the provider's 509/524/529/530/540/598 codes) are documented as temporary — retry after 1-2 minutes (see `errors/marketdata-app-problem-types.yml`).
