---
date: 2026-04-11
description: "Gold Sniper Bot — living goals document, trading system development roadmap"
tags:
  - brain
  - north-star
aliases:
  - Goals
  - Focus
---

# North Star

## Current Focus

- **Validate SR Sniper strategy** — 72.7% WR on 11 trades, need more data + statistical validation (Walk-Forward, Monte Carlo)
- **Connect tools** — TradingView MCP (27 tools), Vibe-Trading (statistical validation), RTK (token savings)
- **Build towards paper trading** — ยังไม่ trade เงินจริง จนกว่าจะ validate ด้วย data มากพอ

## Goals

### Short-term (This Quarter — Q2 2026)

- Validate SR Sniper with Walk-Forward test (เช็ค overfitting)
- Download more historical data (>6 months) for robust testing
- Export SR Sniper → Pine Script → cross-validate on TradingView
- Start paper trading with SR Sniper
- Set up real-time signal alerts (LINE Notify)

### Medium-term (This Half)

- Achieve 100+ paper trades with SR Sniper → confirm 70%+ WR holds
- Tune strategy parameters based on paper trading results
- Build 1-2 additional strategies for comparison/diversification
- Create simple dashboard for monitoring

### Long-term (This Year+)

- Go live with real money (small position size, 1% risk)
- Scale up position size as confidence grows
- Eventually: semi-auto execution via MetaApi
- Document everything for future reference

## Aspirations

- เป็น systematic trader ที่มีวินัย ทำตามระบบ
- มี risk management ที่แข็งแรง ไม่ซ้ำรอยเดิมที่เคยพลาด
- เข้าใจ market structure จริงๆ ไม่ใช่แค่ follow signal

## Anti-goals

- ❌ ไม่ใช้ Martingale เด็ดขาด
- ❌ ไม่ trade ตาม signal จากคนอื่น ใช้ระบบตัวเองเท่านั้น
- ❌ ไม่ overtrade — quality over quantity
- ❌ ไม่ auto-execute ก่อนที่จะ validate ครบ
- ❌ ไม่ scope creep — focus XAUUSD เท่านั้นก่อน

## Shifts Log

| Date | Shift | Reason |
|------|-------|--------|
| 2026-04-11 | Created North Star | Initial Gold Bot vault setup |
| 2026-04-11 | Focus: SR Sniper validation | SR Sniper 72.7% WR — best strategy so far, need validation |
| 2026-04-11 | Added tools: TradingView MCP, Vibe-Trading | Expand capabilities for analysis + validation |
