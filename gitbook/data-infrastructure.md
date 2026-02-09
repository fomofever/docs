# Data Infrastructure

FOMO FEVER aggregates data from multiple sources to provide comprehensive market intelligence. Each provider serves a specific role in the platform's data pipeline.

## Data Providers

### Birdeye API (Primary)

The primary market data provider for all token metrics.

* **Token prices and volumes** — Real-time and historical
* **Liquidity data** — Pool depth and liquidity metrics
* **Trending token lists** — Filtered by market cap category (large, low, micro)
* **Token metadata** — Name, symbol, logo, and descriptive data
* **Token search** — Keyword-based token discovery

Cache TTL: 1 minute for trending data.

### GeckoTerminal API

Free OHLCV candlestick data for charting and fallback token information.

* **Candlestick history** — Used for TradingView Lightweight Charts
* **Fallback token data** — Live price, liquidity, FDV, volume, transaction counts
* **Pool discovery** — Automatically finds the best liquidity pool for each token

Supported intervals: 1m, 5m, 15m, 30m, 1H, 4H, 1D

Cache TTL: 1 minute for chart data, 5 minutes for pool lookups. Includes queue-based rate limiter with 700ms interval and exponential backoff (15–60 seconds).

### Pump.fun API

Bonding curve token data for pre-graduation tokens.

* **Bonding progress** — Percentage of bonding curve completion
* **Token metadata** — Name, symbol, image, social links
* **Price data** — USD price and market cap for bonding-stage tokens

Bonding progress formula: `(1 - (real_token_reserves / 793,100,000,000,000)) × 100`

Cache TTL: 5 minutes.

### Helius API

On-chain transaction activity and engagement metrics.

* **Transaction counts** — Recent transaction activity as engagement signal
* **Enhanced Transactions API** — Detailed transaction history
* **DAS API** — Holder analysis and distribution data

Used in FOMO Meter for real-time on-chain engagement scoring.

### Solana RPC

Direct on-chain queries for token supply and authority verification.

* **Token supply** — Current circulating and total supply
* **Mint authority** — Authority status for safety checks
* **Freeze authority** — Authority status for safety checks

Endpoint: `https://api.mainnet-beta.solana.com`

### Anthropic Claude AI

AI-powered token signal analysis using Replit AI Integrations.

* **Model:** `claude-haiku-4-5`
* **Analysis:** Signal confidence, pattern state, risk flags
* **Cache TTL:** 10 minutes

## Caching Strategy

All external API data is cached with appropriate TTLs to ensure reliability and cost efficiency:

| Data Type            | Cache TTL  | Provider        |
| -------------------- | ---------- | --------------- |
| Trending tokens      | 1 minute   | Birdeye         |
| Chart OHLCV data     | 1 minute   | GeckoTerminal   |
| Pool lookups         | 5 minutes  | GeckoTerminal   |
| Bonding curve data   | 5 minutes  | Pump.fun        |
| AI analysis          | 10 minutes | Anthropic       |
| Stale cache fallback | 10 minutes | GeckoTerminal   |

Stale cache entries are served during rate limit periods to maintain platform availability.
