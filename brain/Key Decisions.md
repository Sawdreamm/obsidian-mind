---
date: 2026-04-11
description: "Gold Sniper Bot — strategy, architecture, and trading rule decisions with rationale"
tags:
  - brain
  - decisions
---

# Key Decisions

## Strategy Decisions

### 2026-04-11: Chose SR Sniper as Primary Strategy
**Context**: Tested 4 strategies (SR Sniper, TLS, High WR PA, Smart Money Sniper)
**Decision**: SR Sniper wins on all metrics that matter for Dream's psychology
**Rationale**:
- 72.7% WR (highest) — Dream needs high WR for confidence
- 1.00R MaxDD (lowest) — never had 2 consecutive losses
- Simple logic (5 steps) — easy to trust and follow
- PF 3.90 — strong edge
**Rejected alternatives**:
- TLS: 9.5% WR = too many losses in a row (12 consecutive), Dream would abandon it
- High WR PA: 68.6% WR but only +1.00R total (R:R 0.5:1 too low)
- Smart Money Sniper: ~15% WR, negative R, too complex
**Link**: [[Strategies]], [[Backtest Results]]

### 2026-04-11: SR Sniper V2 Improvements over V1
**Context**: V1 had 37.5% WR (48 trades, too loose)
**Changes made**:
1. Added EMA slope check (slope > 0.5) — not just price > EMA, EMA must be trending
2. Wick must sweep INTO the level (not just close near it)
3. 1H alignment check — 1H candle must confirm direction
4. Pin bar threshold 75% (was 70%)
5. Level confluence scoring — multiple sources confirming same area
6. R:R capped at 3.0 (prevents unrealistic TP)
**Result**: 72.7% WR (11 trades) — quality over quantity
**Link**: [[Strategies]]

### 2026-04-11: min_level_score=1 (not 2)
**Context**: score=2 gave 100% WR but only 5 trades in 70 days
**Decision**: Use score=1 for more trades while keeping 72.7% WR
**Rationale**: 11 trades/70 days ≈ 1 trade/week is acceptable frequency
**Link**: [[Backtest Results]]

## Architecture Decisions

### 2026-04-11: TradingView MCP for Market Analysis
**Decision**: Connect TradingView MCP (27 tools) via `.mcp.json`
**Rationale**: Real-time screening, sentiment, technical analysis without manual checking
**Setup**: UV + Python 3.12, PYTHONPATH configured
**Link**: [[Tools & Infrastructure]]

### 2026-04-11: Claude Code Skills for Workflow
**Decision**: Create 3 skills: `/analyze-gold`, `/backtest`, `/scan-setup`
**Rationale**: Repeatable workflows as slash commands = consistent execution
**Link**: [[Skills]]

### 2026-04-11: Obsidian Mind for Persistent Memory
**Decision**: Use obsidian-mind vault structure for Gold Bot knowledge
**Rationale**: Claude loses context between sessions — vault preserves decisions, results, and rationale
**Link**: [[Memories]]

### 2026-04-11: No Auto-Execute Until Validated
**Decision**: Bot sends LINE alerts only, Dream trades manually on MT5
**Rationale**: From Trading Journal 2021 — ใจร้อน + ไม่ยอม cut loss = ต้องมีระบบที่ validate แล้วก่อน
**Link**: [[North Star]], [[Trading Lessons]]

## Trading Rule Decisions

### 2026-04-11: London Session Only for Now
**Context**: London WR = 100% (5/5), NY WR = 50% (3/6)
**Decision**: Prioritize London session signals, be cautious with NY
**Rationale**: Small sample but clear edge in London — institutional flow is cleaner

### 2026-04-11: Focus XAUUSD Only
**Decision**: No other pairs until SR Sniper validated with 100+ trades
**Rationale**: Scope creep killed past attempts. One asset, one strategy, master it.
**Link**: [[North Star]]
