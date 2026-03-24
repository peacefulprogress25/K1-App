# Vault Manager Frontend

A Next.js frontend for interacting with Solana vaults through the Ranger/Voltr API.

## Features

- Landing page for the K1 stablecoin product.
- Wallet connection via Solana Wallet Adapter.
- Dashboard for:
  - Viewing vault TVL and interest metrics.
  - Viewing wallet-specific vault balance, pending withdrawals, and actions.
  - Simulating deposits/withdrawals.
  - Building and sending deposit/withdraw transactions.

## Tech Stack

- Next.js 15 (App Router)
- React 19
- TypeScript
- Tailwind CSS
- Solana Wallet Adapter + `@solana/web3.js`

## Prerequisites

- Node.js 20+
- npm (or yarn)
- A Solana wallet browser extension (for dashboard actions)

## Getting Started

1. Install dependencies:

```bash
npm install
```

2. Create your local environment file:

```bash
cp .env.example .env.local
```

3. Update environment values in `.env.local` as needed:

- `NEXT_PUBLIC_RPC_URL` — Solana RPC endpoint.
- `NEXT_PUBLIC_VAULT_PUBKEYS` — comma-separated vault public keys shown in dashboard.
- `NEXT_PUBLIC_RANGER_API_BASE` (optional) — defaults to `https://api.voltr.xyz`.

4. Run the development server:

```bash
npm run dev
```

App will be available at `http://localhost:3005`.

## Scripts

- `npm run dev` — Start development server on port 3005.
- `npm run build` — Build production app.
- `npm run start` — Start production server.
- `npm run lint` — Run Next.js lint checks.

## Project Structure

```text
src/
  app/
    page.tsx                # Landing page
    dashboard/page.tsx      # Vault dashboard UI
    api/vault/[vault]/route.ts  # API routes for vault data
  components/
    WalletProvider.tsx      # Solana wallet provider wiring
  lib/
    ranger-api.ts           # Ranger/Voltr API client helpers
    vault-parse.ts          # UI parsing/format helpers
```

## Notes

- The dashboard expects valid vault public keys and API availability for full data rendering.
- Some vault operations are multi-step (request withdrawal then claim withdrawal) based on API behavior.
