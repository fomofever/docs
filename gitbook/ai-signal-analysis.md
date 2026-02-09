# AI Signal Analysis

FOMO FEVER integrates Anthropic's Claude AI to provide automated market signal classification for every tracked token. The AI layer processes real-time market data and returns structured analysis.

## Analysis Output

Each token analysis produces three data points:

### Signal Confidence (0–100)

A numerical score representing the strength and consistency of the momentum classification. Higher confidence means the AI has stronger evidence for its pattern assessment.

### Pattern State

Every token is classified into one of four market phases:

| Pattern State    | Description                                             |
| ---------------- | ------------------------------------------------------- |
| **Accumulation** | Price flat or down, but volume remains active            |
| **Expansion**    | Price rising with strong volume confirmation             |
| **Distribution** | Price elevated with signs of sell pressure                |
| **Fading**       | Both price and volume declining                          |

### Risk Flags

Automatically flagged when abnormal conditions are detected:

* Low liquidity relative to trading volume
* Concentrated holder distributions
* Extreme volatility patterns
* Unusual volume spikes without organic momentum

## Technical Details

* **Model:** `claude-haiku-4-5` — Selected for fast, cost-effective analysis at scale
* **Cache TTL:** 10 minutes — Balances data freshness with API cost efficiency
* **Integration:** Replit AI Integrations — No separate API key required, billed to Replit credits
* **Endpoint:** `POST /api/analyze-tokens` — Accepts an array of token data for batch analysis
