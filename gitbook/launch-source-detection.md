# Launch Source Detection

FOMO FEVER automatically detects a token's origin platform by analyzing its mint address suffix. This classification determines the token's expected migration path and lifecycle behavior.

## Platform Detection

| Suffix   | Platform    | Migration Path                          |
| -------- | ----------- | --------------------------------------- |
| `pump`   | Pump.fun    | Bonding curve → PumpSwap                |
| `bonk`   | LetsBonk    | Raydium LaunchLab → Raydium V4/CPMM     |
| `bags`   | Bags.fm     | Meteora DBC → Meteora DEX               |
| Other    | Standard SPL | Direct DEX listing                      |

## Token Filtering

By default, FOMO FEVER only displays tokens with contract addresses ending in `pump`, `bonk`, or `bags`. This ensures the platform focuses on tokens launched through recognized Solana launchpads.

Tokens with other suffixes can be added manually by platform administrators for special cases.

## Lifecycle Stages

Each token is automatically classified into one of three lifecycle stages based on its current on-chain state:

### Bonding

Token is still in its bonding curve on the launch platform. No liquidity pool has been detected on a DEX.

* Pump.fun tokens graduate at 100% bonding curve completion
* LetsBonk tokens use Raydium LaunchLab bonding mechanics
* Bags.fm tokens use Meteora Dynamic Bonding Curves (DBC)

### Migrated

Token has graduated from its bonding curve and migrated to DEX trading within the last 24 hours.

* Pump.fun → PumpSwap
* LetsBonk → Raydium V4 or CPMM
* Bags.fm → Meteora DEX

### DEX Live

Token has been actively trading on a decentralized exchange for more than 24 hours. This is the most mature lifecycle stage.

## Detection Method

Lifecycle detection uses the Birdeye and GeckoTerminal APIs to check for active liquidity pools. When a pool is detected, the token's lifecycle stage transitions from `bonding` to `migrated`, and after 24 hours of DEX activity, to `dex_live`.
