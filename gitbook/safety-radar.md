# Safety Radar

Every token on the platform undergoes automated safety checks at regular intervals. The Safety Radar evaluates five on-chain security indicators to help participants assess project legitimacy.

## Security Checks

### 1. Mint Authority

Verifies whether the token's mint authority has been revoked. When mint authority is active, the token creator can mint unlimited additional supply, diluting existing holders.

* **Pass:** Mint authority revoked
* **Fail:** Mint authority still active

### 2. Freeze Authority

Checks whether the freeze authority has been revoked. Active freeze authority allows the creator to freeze any holder's token account, preventing them from transferring or selling.

* **Pass:** Freeze authority revoked
* **Fail:** Freeze authority still active

### 3. Liquidity Pool Detection

Confirms that the token has active liquidity on a decentralized exchange. Tokens without LP cannot be freely traded and may be in a pre-launch or bonding curve state.

Supported DEXs:

* Raydium (V4, CPMM)
* Orca (Whirlpool)
* Meteora (DLMM, Dynamic)
* PumpSwap

### 4. LP Lock / Burn Status

Evaluates whether liquidity pool tokens are locked in a vesting contract or burned. Unlocked LP allows the creator to remove liquidity at any time (rug pull vector).

* **Burned:** LP tokens sent to a burn address — permanent and irreversible
* **Locked:** LP tokens held in a time-lock contract — temporary protection
* **Unlocked:** LP tokens in creator wallet — highest risk

### 5. Holder Distribution

Analyzes the concentration of token holdings among top wallets. Tokens where a single non-exchange wallet holds a disproportionate share of supply carry higher manipulation risk.

## Check Frequency

Trust checks run every **15 minutes** for active tokens using:

* **Solana RPC** — Authority data (mint/freeze status)
* **Birdeye / GeckoTerminal** — LP detection and liquidity data
* **Helius DAS API** — Holder analysis and distribution metrics
