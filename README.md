# Market Data (marketdata-app)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
