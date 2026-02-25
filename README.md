# Bitpanda Skill

An agent skill for querying Bitpanda accounts via the Bitpanda API. Covers all read-only endpoints: portfolio, balances, trades, transactions, asset info, and live prices.

This skill follows the [Agent Skills Open Standard](https://agentskills.io/home).

## Features

- **Portfolio overview** — aggregated holdings with EUR valuations, combining regular, staking, and index wallets per asset
- **Trade history** — buy/sell history with asset name resolution, type classification, and date filtering
- **Live prices** — current prices and daily changes for any listed asset
- **Transactions** — full transaction log including rewards, deposits, withdrawals, and staking
- **Asset lookup** — resolve asset IDs to names and symbols

All commands return JSON and are read-only — no trading, orders, or write operations.

## Requirements

- `curl`
- `jq`
- A Bitpanda API key (generate one at https://web.bitpanda.com/my-account/apikey)

## Setup

Set your API key as an environment variable:

```bash
export BITPANDA_API_KEY="your-api-key-here"
```

Verify it works:

```bash
bash bitpanda/scripts/bitpanda.sh balances --page-size 5
```

## Commands

| Command | Description |
|---|---|
| `portfolio` | Aggregated holdings with EUR prices and totals |
| `price <SYMBOL>` | Price, currency, and daily change for a single asset |
| `prices` | Prices for held assets (`--all` for everything) |
| `trades` | Buy/sell history with filtering by operation, asset type, date range |
| `balances` | Raw wallet list with pagination and filtering |
| `all-transactions` | Full transaction log with pagination and filtering |
| `asset <asset_id>` | Single asset info (name, symbol) |

## Project Structure

```
bitpanda/
├── SKILL.md              # Skill manifest and agent instructions
├── scripts/
│   └── bitpanda.sh       # CLI implementation
└── references/
    └── api_reference.md   # API endpoint documentation
```

## License

See [LICENSE](LICENSE) for details.
