---
name: Analyze an options chain without exhausting credits
description: Look up option expirations and strikes, pull a filtered options chain, and quote individual contracts from the Market Data API while controlling per-symbol credit consumption.
api: openapi/marketdata-app-options-api-openapi.yml
operations: [getOptionExpirations, getOptionStrikes, getOptionChain, getOptionQuote, getOptionLookup]
generated: '2026-07-22'
method: generated
---

# Analyze an options chain without exhausting credits

## Auth

Send `Authorization: Bearer <token>`. For testing without a token, use any AAPL contract (e.g. `AAPL271217C00250000`).

## Steps

1. **Discover expirations** — `getOptionExpirations`: `GET /options/expirations/{underlying}/`.
2. **Discover strikes** — `getOptionStrikes`: `GET /options/strikes/{underlying}/`, optionally scoped to one expiration.
3. **Pull a filtered chain** — `getOptionChain`: `GET /options/chain/{underlying}/` using filters (expiration, `strikeLimit`, strike range, delta, side, liquidity) to narrow the result. **Never pull an unfiltered chain of a large underlying** (the SPX chain alone has 20,000+ contracts and each contract with bid/ask/mid/last columns consumes one credit).
4. **Quote one contract** — `getOptionQuote`: `GET /options/quotes/{optionSymbol}/` with the OCC symbol.
5. **Resolve a human description to an OCC symbol** — `getOptionLookup`: `GET /options/lookup/{userInput}/` (e.g. "AAPL 12/17/2027 250 Call").

## Rules

- Exclude `bid`, `ask`, `mid`, and `last` via the `columns` parameter when you do not need prices — multi-symbol responses without those columns bill as a single credit.
- Treat HTTP 203 as success; errors use `{"s": "error", "errmsg": "..."}`.
- Paid plans can use `mode=cached` for reduced-cost chain snapshots (not available on trial plans).
- OCC symbol format: underlying + `yymmdd` expiration + `C`/`P` + strike x1000 zero-padded (see `data-model/marketdata-app-data-model.yml`).
