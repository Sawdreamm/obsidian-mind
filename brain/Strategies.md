---
date: 2026-04-11
description: "All trading strategies tested — logic, parameters, and performance comparison"
tags:
  - brain
  - strategies
---

# Strategies

## Active Strategy

### SR Sniper (Primary) ⭐
**File**: `strategy/sr_sniper.py`
**Timeframe**: 15M entry, 1H for trend + zones
**Logic**: Session → EMA50 Trend+Slope → Key Level (zone/round/EMA) → Rejection Candle → R:R 1.0+
**Win Rate**: 72.7% (8W/3L from 11 trades)
**Key Params**: `trend_ema_period=50, pin_bar_wick_pct=0.75, min_rr=1.0, cooldown=16`
**Strengths**: Highest WR, lowest DD, simple logic
**Weakness**: Few trades (11 in 2 months), needs more data
**Link**: [[Backtest Results]], [[Key Decisions]]

## Archived Strategies

### TLS (Trend → Level → Signal)
**File**: `strategy/tls_plugin.py` + `strategy/tls.py`
**Logic**: 6 filters — Session + DXY + HTF Trend + Zone/Fib + Sweep + Entry Candle + RSI Div
**Win Rate**: 9.5% (2W/19L) but Total R +42.64 (lottery-like wins)
**Verdict**: Too low WR for Dream's psychology. Big wins come from R:R 23-38 trades.
**Link**: [[Backtest Results]]

### High Win-Rate PA (EMA Pullback Rejection)
**File**: `strategy/high_winrate_pa.py`
**Logic**: EMA 35/75 crossover → Detachment → Pullback to EMA → Rejection → R:R 0.5:1
**Win Rate**: 68.6% (24W/11L) but Total R +1.00 only (R:R too low)
**Verdict**: Good WR but barely profitable due to 0.5:1 R:R
**Link**: [[Backtest Results]]

### Smart Money Sniper
**File**: `strategy/smart_money_sniper.py`
**Logic**: Top-Down Trend → Zones+Fib+50SMA → Sweep → Entry Pattern + RSI Div
**Win Rate**: ~15%, negative total R
**Verdict**: Too many signals, no session filter, needs major tuning
**Link**: [[Backtest Results]]

## Strategy Comparison Table

| Strategy | Trades | WR% | PF | Total R | Max DD | Consec Loss |
|---|---|---|---|---|---|---|
| **SR Sniper** | 11 | **72.7%** | **3.90** | +8.71 | **1.00R** | **1** |
| High WR PA | 35 | 68.6% | 1.09 | +1.00 | 4.50R | 4 |
| TLS | 21 | 9.5% | 3.24 | +42.64 | 12.00R | 12 |
| Smart Money | ~52 | ~15% | <1.0 | negative | high | high |

## Strategy Design Principles (Learned)

1. **Simple beats complex** — SR Sniper (5 steps) beats SMC (7+ steps)
2. **Quality over quantity** — 11 high-quality trades > 52 low-quality trades
3. **R:R sweet spot** — 1.0-3.0 range. Not 0.5 (PA) or 2.0+ only (TLS)
4. **Session filter is critical** — London + NY session only = cleaner signals
5. **EMA slope matters** — not just price > EMA, but EMA must be trending
6. **Wick must touch level** — proximity alone isn't enough, need actual sweep/touch
