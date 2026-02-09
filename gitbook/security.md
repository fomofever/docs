# Security

FOMO FEVER implements multiple security layers to protect users and ensure platform integrity.

## Authentication & Authorization

### Admin Operations

* **Server-side API key validation** — All admin endpoints require the `x-admin-key` header matching the `ADMIN_API_KEY` secret
* **No client-side secrets** — Admin authentication is verified entirely on the server

### User Actions

* **Wallet-based verification** — Solana wallet signatures confirm user identity for on-chain operations
* **No stored passwords** — Platform does not maintain user accounts with passwords

## Anti-Abuse Measures

### Cloudflare Turnstile CAPTCHA

All user-facing actions that create or modify data require Cloudflare Turnstile verification. This includes:

* Profile claiming
* Trust tier upgrade requests
* Email subscriptions

### Bot Detection

Server-side analysis of request patterns identifies and blocks automated abuse:

* Request timing analysis
* Header fingerprinting
* Rate limiting per IP and wallet

### Rate Limiting

API endpoints are rate-limited to prevent abuse and protect upstream data providers:

* GeckoTerminal: Queue-based limiter with 700ms interval
* Exponential backoff: 15–60 seconds during rate limit periods
* Stale cache serving during rate limit windows

## Data Integrity

### On-Chain Verification

All burn transactions are verified directly on Solana mainnet:

* Transaction signature validation
* Burn amount confirmation
* Destination address verification (must be a known burn address)

### Input Validation

* **Zod schemas** — Every API endpoint validates request bodies using Zod schemas from `drizzle-zod`
* **Type safety** — Shared TypeScript types between frontend and backend prevent data mismatches
* **SQL injection prevention** — Drizzle ORM parameterizes all database queries

### Session Management

* **PostgreSQL-backed sessions** — Session data stored securely in the database via `connect-pg-simple`
* **Secure cookies** — HTTP-only, secure, same-site cookie configuration

## Infrastructure

* **HTTPS** — All traffic encrypted via TLS
* **Environment secrets** — API keys and sensitive configuration stored as encrypted Replit secrets
* **No exposed secrets** — All secret access is server-side only
