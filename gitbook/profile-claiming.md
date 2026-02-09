# Profile Claiming

Token projects can claim their profile on FOMO FEVER to add branding, social links, and descriptions. Profile claiming is exclusively available through $FOMO token burns — reinforcing the deflationary utility of the token.

## Claiming Process

1. **Connect Wallet** — Project team connects their Solana wallet to FOMO FEVER
2. **Verify Ownership** — Wallet-based ownership verification confirms the caller's association with the token
3. **Burn $FOMO** — A minimum $FOMO burn is required to activate profile claiming
4. **Complete Profile** — Upload branding assets and fill in project information
5. **CAPTCHA Verification** — Cloudflare Turnstile CAPTCHA prevents automated abuse
6. **Confirmation** — Email receipt is sent confirming the profile claim

## Profile Features

Claimed profiles include:

### Visual Branding

* **Logo** — Custom token logo uploaded directly or via URL
* **Banner** — Profile banner image for enhanced visual presence

Images are uploaded via Replit Object Storage with presigned URL flow for secure, direct uploads.

### Project Information

* **Description** — Detailed project description visible on the token's page
* **Website** — Official project website link
* **Twitter** — Project's Twitter/X profile link
* **Telegram** — Community Telegram group link

## Security Measures

Profile claiming includes multiple security layers:

* **Cloudflare Turnstile CAPTCHA** — Prevents bot-driven fake claims
* **Bot Detection** — Server-side analysis of request patterns
* **Wallet Verification** — On-chain ownership confirmation
* **Burn Requirement** — Economic cost prevents spam claims
* **Email Receipts** — Sent via Resend for confirmation and audit trail
