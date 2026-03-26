# Lattiq x402 Trading Signals

**MCP server for regime-aware futures trading signals.** Pay per-request in USDC via x402 micropayments on Base network.

Live at **https://api.lattiq.ai**

## What It Does

Lattiq provides quantitative trading intelligence for ES1 and NQ futures through a 5-state Hidden Markov Model and 15+ battle-tested strategies.

| Endpoint | Method | Price | Description |
|----------|--------|-------|-------------|
| `/regime` | GET | $0.01 | Current HMM regime state (bull/bear/neutral/volatile/crash) |
| `/signal` | GET | $0.02 | Latest strategy signal with entry/exit levels |
| `/backtest` | POST | $0.10 | Full walk-forward backtest with Monte Carlo |
| `/monte-carlo` | POST | $0.05 | Monte Carlo simulation on equity curves |
| `/correlation` | GET | $0.02 | ES1/NQ correlation and divergence analysis |
| `/market-brief` | GET | $0.05 | Data-driven market analysis |
| `/health` | GET | Free | API health check |

## How It Works

All paid endpoints use the [x402 protocol](https://x402.org). AI agents pay automatically in USDC on Base network — no API keys, no subscriptions, no accounts.

```
GET https://api.lattiq.ai/regime
→ 402 Payment Required
→ { "accepts": [{ "network": "base", "currency": "USDC", "amount": "0.01" }] }

GET https://api.lattiq.ai/regime
X-PAYMENT: <x402-payment-header>
→ 200 OK
→ { "regime": "bullish", "confidence": 0.87, ... }
```

## MCP Integration

Add Lattiq to any MCP-compatible AI agent:

**Manifest URL:** `https://api.lattiq.ai/.well-known/mcp/manifest.json`

**Available tools:**
- `get_regime` — Current market regime classification
- `get_signal` — Latest trading signal
- `run_backtest` — Walk-forward backtest with custom parameters
- `run_monte_carlo` — Monte Carlo equity simulation
- `get_correlation` — Cross-asset correlation analysis
- `get_market_brief` — Comprehensive market analysis

## Discovery

- **MCP Manifest:** https://api.lattiq.ai/.well-known/mcp/manifest.json
- **x402 Descriptor:** https://api.lattiq.ai/.well-known/x402.json
- **Health Check:** https://api.lattiq.ai/health

## Technical Details

- **Payment network:** Base (Ethereum L2)
- **Currency:** USDC
- **Wallet:** `0x1624FCE53E0419C32eB3b62B139AcC8bb8fCDE4C`
- **Regime model:** 5-state Hidden Markov Model retrained per fold
- **Strategies:** 15 quantitative strategies including squeeze momentum, regression channels, market structure
- **Data:** ES1/NQ futures (hourly and daily timeframes)

## Contact

- **Email:** api@lattiq.ai
- **Website:** https://api.lattiq.ai
