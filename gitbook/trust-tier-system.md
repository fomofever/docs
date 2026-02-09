# Trust Tier System

The Trust Tier System is FOMO FEVER's burn-based verification layer. Token projects can burn $FOMO tokens to earn trust status, which provides ranking boosts and visual credibility indicators on the platform.

## Tier Structure

| Tier                  | USD Burned | Score Multiplier | Benefits                      |
| --------------------- | ---------- | ---------------- | ----------------------------- |
| **Tier 0** (Unverified) | $0         | 1.0x             | Base listing                  |
| **Tier 1** (Bronze)     | $100       | 1.05x            | Trust badge + minor boost     |
| **Tier 2** (Silver)     | $250       | 1.12x            | Enhanced badge + moderate boost |
| **Tier 3** (Gold)       | $500       | 1.25x            | Premium badge + maximum boost |

Tier thresholds are based on the USD value of $FOMO burned, calculated at the time of the burn transaction using real-time market price.

## Burn Verification Flow

1. **Tier Selection** — User selects their target tier and connects their Solana wallet
2. **Amount Calculation** — The required $FOMO burn amount is calculated based on the current market price
3. **Transaction Confirmation** — User confirms the burn transaction, sending $FOMO tokens to a burn address
4. **On-Chain Verification** — Backend verifies the transaction signature on Solana mainnet
5. **Tier Upgrade** — Trust tier is upgraded and the score multiplier is applied to the token's FOMO score
6. **Email Receipt** — A confirmation email receipt is sent via Resend

## Score Multiplier

The trust tier multiplier is applied to a token's base FOMO score:

```
Boosted Score = Base FOMO Score × Tier Multiplier
```

The boosted score is capped at 100 (the maximum FOMO score). This means a Tier 3 (Gold) token with a base score of 80 would receive:

```
80 × 1.25 = 100 (capped)
```

## Deflationary Impact

Every burn permanently removes $FOMO tokens from circulation. As more projects verify through the Trust Tier System, the total supply of $FOMO decreases, creating natural deflationary pressure.

All burn transactions are:

* Recorded on-chain (Solana mainnet)
* Tracked in the platform database
* Publicly verifiable via transaction signature
