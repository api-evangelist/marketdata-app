# Market Data (marketdata-app)

Market Data (marketdata.app) is a financial market data provider offering a REST API for real-time and historical U.S. stock, options, and index data. The API (base `https://api.marketdata.app/v1`, authenticated with a Bearer token) covers stock candles and quotes - single and bulk - plus earnings and news; full options chains with per-contract quotes, expirations, strikes, and OCC symbol lookup; index candles and quotes; and market open/closed status. Responses are delivered as JSON or CSV.

Market Data is a commercial hosted service (not open source), but it publishes official open-source client SDKs (Python, Go, and PHP) under the [MarketDataApp GitHub organization](https://github.com/MarketDataApp). It is priced on a daily API-credit model: every successful call costs at least one credit, and multi-symbol responses (bulk quotes, bulk candles, and options chains) consume **one credit per symbol returned** - so a full option chain such as SPX can cost thousands of credits in a single request. A 30-day trial (no credit card), a Free Forever tier (100 requests/day), and paid Starter, Trader, Quant, and Prime plans are available. Real-time data is excluded from free trials for non-professional users due to exchange regulations.

**Access model note:** Registration is required for a token, though a handful of symbols (AAPL, AAPL option contracts, VFINX) can be tried without an account. There is **no public WebSocket or streaming API** - "real-time" means a live value returned synchronously from a REST call. Watch for HTTP `203 Non-Authoritative Information`, which Market Data returns from its caching tier and which clients must treat the same as `200 OK`.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/marketdata-app/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/marketdata-app/refs/heads/main/apis.yml)

## Tags

- Market Data
- Financial Data
- Stocks
- Options
- Indices
- Real-Time Data
- Historical Data
- Quotes

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Market Data Stocks API

Real-time and historical stock data - OHLCV candles at any resolution, single and bulk quotes, corporate earnings, and news - for U.S. equities. Multi-symbol bulk endpoints consume one API credit per symbol returned.

- **Human URL:** [https://www.marketdata.app/docs/api/stocks](https://www.marketdata.app/docs/api/stocks)
- **Base URL:** `https://api.marketdata.app/v1/stocks`

#### Tags

- Stocks
- Market Data
- Financial Data
- Quotes
- Candles

#### Properties

- [Documentation](https://www.marketdata.app/docs/api/stocks)
- [API Reference](https://www.marketdata.app/docs/api/stocks/candles)
- [OpenAPI](openapi/marketdata-app-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marketdata-app.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marketdata-app.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Market Data Options API

Full options coverage - end-of-day and real-time option chains with extensive filtering, per-contract quotes with Greeks and open interest, expiration and strike lists, and OCC option-symbol lookup. Each option symbol returned in a chain consumes an API credit.

- **Human URL:** [https://www.marketdata.app/docs/api/options](https://www.marketdata.app/docs/api/options)
- **Base URL:** `https://api.marketdata.app/v1/options`

#### Tags

- Options
- Market Data
- Financial Data
- Options Chain
- Greeks

#### Properties

- [Documentation](https://www.marketdata.app/docs/api/options)
- [API Reference](https://www.marketdata.app/docs/api/options/chain)
- [OpenAPI](openapi/marketdata-app-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marketdata-app.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marketdata-app.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Market Data Indices API

Real-time and historical index data - OHLC candles at any resolution and quotes for market indices such as VIX and SPX.

- **Human URL:** [https://www.marketdata.app/docs/api/indices](https://www.marketdata.app/docs/api/indices)
- **Base URL:** `https://api.marketdata.app/v1/indices`

#### Tags

- Indices
- Market Data
- Financial Data
- Real-Time Data

#### Properties

- [Documentation](https://www.marketdata.app/docs/api/indices)
- [OpenAPI](openapi/marketdata-app-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marketdata-app.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marketdata-app.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Market Data Markets API

Reference and status data about the markets Market Data covers - the market status endpoint reports open or closed for a given date or date range, per country, honoring weekends and exchange holidays.

- **Human URL:** [https://www.marketdata.app/docs/api/markets/status](https://www.marketdata.app/docs/api/markets/status)
- **Base URL:** `https://api.marketdata.app/v1/markets`

#### Tags

- Markets
- Market Status
- Reference Data

#### Properties

- [Documentation](https://www.marketdata.app/docs/api/markets/status)
- [OpenAPI](openapi/marketdata-app-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/marketdata-app.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/marketdata-app.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Authentication](authentication/marketdata-app-authentication.yml)
- [GitHub Organization](https://github.com/MarketDataApp)
- [LinkedIn](https://www.linkedin.com/company/marketdataapp)
- [Website](https://www.marketdata.app)
- [Documentation](https://www.marketdata.app/docs/api)
- [Sign Up](https://www.marketdata.app/dashboard/)
- [Plans](plans/marketdata-app-plans-pricing.yml)
- [Rate Limits](rate-limits/marketdata-app-rate-limits.yml)
- [Fin Ops](finops/marketdata-app-finops.yml)
- [Pricing](https://www.marketdata.app/pricing/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
