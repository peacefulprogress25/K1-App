# K1 App (Vault Manager Frontend)

A Next.js frontend for interacting with Solana vaults through the Voltr Ranger API and the `@voltr/vault-sdk`.

## What this app does

- Presents the K1 landing page.
- Connects a Solana wallet using Wallet Adapter.
- Provides a dashboard to:
  - View vault TVL and interest metrics.
  - View wallet-specific balances and pending withdrawals.
  - Simulate deposits and withdrawals.
  - Build/send deposit and withdrawal transactions.

## Tech stack

- Next.js 15 (App Router)
- React 19 + TypeScript
- Tailwind CSS
- Solana Wallet Adapter
- `@solana/web3.js`
- `@voltr/vault-sdk`

## Prerequisites

- Node.js 20+
- npm or yarn
- A Solana wallet browser extension (for dashboard interactions)

## Local development

1. Install dependencies:

   ```bash
   npm install
   ```

2. Create local environment config:

   ```bash
   cp .env.example .env.local
   ```

3. Set environment values in `.env.local`:

   - `NEXT_PUBLIC_RPC_URL`: Solana RPC endpoint.
   - `NEXT_PUBLIC_VAULT_PUBKEYS`: Comma-separated vault public keys shown in dashboard.
   - `NEXT_PUBLIC_RANGER_API_BASE` (optional): Ranger API base URL (defaults to `https://api.voltr.xyz`).

4. Start the dev server:

   ```bash
   npm run dev
   ```

5. Open the app:

   - `http://localhost:3005`

## Available scripts

- `npm run dev` — Start development server on port `3005`
- `npm run build` — Build production app
- `npm run start` — Start production server
- `npm run lint` — Run lint checks

## Project structure

```text
src/
  app/
    page.tsx                    # Landing page
    dashboard/page.tsx          # Vault dashboard UI
    api/vault/[vault]/route.ts  # API route for vault data/actions
  components/
    WalletProvider.tsx          # Solana wallet adapter wiring
  lib/
    ranger-api.ts               # Ranger/Voltr API helpers
    vault-parse.ts              # Vault response parsers/formatters
public/
  icons/                        # Social and external icons
```

## Notes

- Vault rendering depends on valid vault public keys and API availability.
- Some withdrawal flows are multi-step (request first, claim later).
