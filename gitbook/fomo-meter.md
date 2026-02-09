# FOMO Meter

The FOMO Meter is the platform's flagship feature — a dynamic scoring engine that assigns every tracked token a score from 0 to 100 based on real market activity.

## Scoring Components

The FOMO Score is computed from four weighted components:

| Component        | Weight    | Data Source                              |
| ---------------- | --------- | ---------------------------------------- |
| Volume Score     | 0–30 pts  | 24h trading volume via Birdeye API       |
| Momentum Score   | 0–35 pts  | 24h price change percentage              |
| Liquidity Score  | 0–25 pts  | Token liquidity depth via Birdeye/GeckoTerminal |
| Activity Bonus   | 0–10 pts  | On-chain transaction count via Helius    |

### Volume Score Breakdown

| 24h Volume         | Points |
| ------------------ | ------ |
| > $500,000         | 30     |
| > $200,000         | 25     |
| > $100,000         | 18     |
| > $50,000          | 12     |
| > $10,000          | 6      |
| < $10,000          | 2      |

### Momentum Score Breakdown

| 24h Price Change   | Points |
| ------------------ | ------ |
| > +50%             | 35     |
| > +25%             | 28     |
| > +10%             | 20     |
| > 0%               | 12     |
| > -10%             | 5      |
| < -10%             | 0      |

## FOMO Tiers

Tokens are classified into four tiers based on their total score:

| Tier       | Score Range | Color  | Signal                                        |
| ---------- | ----------- | ------ | --------------------------------------------- |
| **LOW**       | 0–39        | Green  | Minimal activity, early stage or declining interest |
| **MODERATE**  | 40–59       | Yellow | Growing attention, building momentum          |
| **HIGH**      | 60–79       | Orange | Significant volume and price action           |
| **EXTREME**   | 80–100      | Red    | Peak activity, elevated caution advised       |

## Trust Tier Boost

Tokens with verified Trust Tiers receive a score multiplier applied to their base FOMO score. This rewards projects that have demonstrated commitment through $FOMO burns. The boosted score is capped at 100.
