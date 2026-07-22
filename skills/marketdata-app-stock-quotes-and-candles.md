---
name: Fetch stock quotes and historical candles
description: Retrieve a real-time stock quote, bulk quotes for a watchlist, and historical OHLCV candles from the Market Data API, handling its credit and caching semantics correctly.
api: openapi/marketdata-app-stocks-api-openapi.yml
operations: [getStockQuote, getStockBulkQuotes, getStockCandles, getStockBulkCandles]
generated: '2026-07-22'
method: generated
---

# Fetch stock quotes and historical candles

## Auth

Send `Authorization: Bearer <token>` on every request (token from the Market Data dashboard). For testing without a token, use the demo symbol `AAPL` (historical data only).

## Steps

1. **Single quote** — `getStockQuote`: `GET /stocks/quotes/{symbol}/` (e.g. `AAPL`). Response is a columnar envelope of parallel arrays with `bid`, `ask`, `mid`, `last`.
2. **Watchlist quotes** — `getStockBulkQuotes`: `GET /stocks/bulkquotes/` with the `symbols` query parameter. Each symbol in the response consumes one API credit; keep watchlists sized to your plan.
3. **Historical candles** — `getStockCandles`: `GET /stocks/candles/{resolution}/{symbol}/` with `from`/`to` dates. Resolutions include `D`, `W`, `M`, and minute/hour values. Daily candles default to the last 252 bars; use `limit` (max 50,000) and `offset` to page.
4. **Bulk end-of-day candles** — `getStockBulkCandles`: `GET /stocks/bulkcandles/{resolution}/` for many symbols at once.

## Rules

- Treat HTTP **203** exactly like 200 (cache-tier response) and **204** as a cache miss when `mode=cached` was requested.
- Errors arrive as `{"s": "error", "errmsg": "..."}` — see `errors/marketdata-app-problem-types.yml`.
- Watch `X-Api-Ratelimit-Remaining` and `X-Api-Ratelimit-Reset`; daily credit windows reset at 9:30 AM Eastern. Keep concurrency at or below 50.
- All timestamps are `America/New_York`; pick `dateformat=timestamp|unix|spreadsheet` as needed.
- One IP address per account — do not fan out across hosts with the same token.
