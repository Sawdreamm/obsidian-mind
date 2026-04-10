---
date: 2026-04-11
description: "Historical backtest results — all strategies, all parameter variants"
tags:
  - brain
  - backtest
---

# Backtest Results

## SR Sniper — Primary Results

### 2026-04-11: SR Sniper V2 (Default Params)
**Data**: XAUUSD 15M (2026-01-29 → 2026-04-10, ~70 days)
**Params**: `ema=50, slope_lb=5, slope_min=0.5, proximity=0.1%, pin_bar=75%, min_rr=1.0, cooldown=16`
| Metric | Value |
|---|---|
| Total Trades | 11 |
| Wins / Losses | 8 / 3 |
| Win Rate | 72.7% |
| Profit Factor | 3.90 |
| Total R | +8.71 |
| Avg R/Trade | +0.79 |
| Best Trade | +2.98R |
| Worst Trade | -1.00R |
| Max Consec Wins | 5 |
| Max Consec Losses | 1 |
| Max Drawdown | 1.00R |
| Avg Duration | 1.0 hours |
| BUY WR | 100% (2/2) |
| SELL WR | 66.7% (6/9) |
| London WR | 100% (5/5) |
| NY WR | 50% (3/6) |

**Notable**: London session = 100% WR. Never had 2 consecutive losses.

### SR Sniper V2 Parameter Variants (2026-04-11)
| Config | Trades | WR% | PF | Total R | MaxDD |
|---|---|---|---|---|---|
| score=1 cd=16 (default) | 11 | 72.7% | 3.90 | +8.71 | 1.00R |
| score=1 cd=12 | 11 | 72.7% | 3.90 | +8.71 | 1.00R |
| score=1 cd=10 prox=0.12% | 14 | 64.3% | 2.94 | +9.71 | 3.00R |
| score=2 cd=16 (strict) | 5 | 100% | inf | +7.50 | 0.00R |

### SR Sniper V1 (2026-04-11 — before improvements)
**WR**: 37.5% (18W/30L from 48 trades) — too loose, round numbers + wide proximity

## Other Strategy Results

### TLS (2026-04-11)
**Data**: Same period
**Result**: 21 trades, 9.5% WR, PF 3.24, Total R +42.64, MaxDD 12.00R

### High Win-Rate PA (2026-04-11)
**Data**: XAUUSD 4H (2025-08-13 → 2026-04-10, ~8 months)
**Result**: 35 trades, 68.6% WR, PF 1.09, Total R +1.00, MaxDD 4.50R

### Smart Money Sniper (2026-04-11)
**Data**: XAUUSD 15M, same period as TLS
**Result**: ~52 trades, ~15% WR, negative total R

## Data Available

| File | Rows | Period | Source |
|---|---|---|---|
| GCF_15m.csv | 4544 | 2026-01-29 → 2026-04-10 | yfinance GC=F |
| GCF_1h.csv | 3723 | 2025-08-13 → 2026-04-10 | yfinance GC=F |
| GCF_4h.csv | 1011 | 2025-08-13 → 2026-04-10 | Resampled from 1H |
| DXYNYB_1h.csv | 3868 | 2025-08-13 → 2026-04-10 | yfinance DX-Y.NYB |

**Limitation**: 15M data only 60 days (yfinance limit). Need more data for robust validation.

## Validation TODO

- [ ] Walk-Forward test (split data into train/test)
- [ ] Monte Carlo permutation test
- [ ] Bootstrap Sharpe CI
- [ ] Download longer historical data
- [ ] Cross-validate on TradingView via Pine Script
