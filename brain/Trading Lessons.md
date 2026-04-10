---
date: 2026-04-11
description: "Dream's trading mistakes from 2021 journal — rules and safeguards built into the system"
tags:
  - brain
  - trading
  - lessons
---

# Trading Lessons

From Dream's Trading Journal 2021. These mistakes shaped the system's design.

## Past Mistakes (Never Repeat)

### 1. ใจร้อน — Revenge Trading
**What happened**: เข้าเพราะอยากได้คืนจากที่เสียไป
**Safeguard**: Cooldown period = 16 candles (4 hours) after every trade
**System rule**: Bot won't generate signal within cooldown window, period.

### 2. ไม่เช็คแนวรับให้ดี — Poor Level Identification  
**What happened**: เข้า trade ที่ level ไม่แข็งแรง
**Safeguard**: Level confluence scoring — single source level = risky, multiple = confident
**System rule**: Wick must actually sweep/touch the level, not just "be near" it

### 3. Lot Size เยอะเกิน — Overleveraging
**What happened**: ใช้ lot ใหญ่เกินไป หวัง "รวยเร็ว"
**Safeguard**: Fixed fractional method — risk 1-2% per trade only
**System rule**: `lot_size = risk_amount / (pip_diff * pip_value)` — calculated, not guessed

### 4. ไม่ยอม Cut Loss — Holding Losers
**What happened**: เมื่อผิดทาง ไม่ยอมตัด กลายเป็นขาดทุนหนัก
**Safeguard**: SL set at entry, never moved further away
**System rule**: SL = beyond rejection wick + buffer. Once set, NEVER widen.

### 5. เทรดหลายคู่พร้อมกัน — Overtrading
**What happened**: กระจาย focus ไปหลายคู่ ไม่เก่งสักคู่
**Safeguard**: XAUUSD only — ไม่มี multi-asset จนกว่าจะ master ตัวนี้
**System rule**: One asset, one strategy, one focus.

### 6. เคยใช้ Martingale — Doubling Down
**What happened**: เพิ่ม lot หลังขาดทุน หวังจะได้คืน → ขาดทุนหนักขึ้น
**Safeguard**: Fixed lot size per trade, never increase after loss
**System rule**: ❌ BANNED. ห้ามใช้ Martingale เด็ดขาด.

### 7. เทรดตาม Signal คนอื่น — Following Others
**What happened**: ตาม signal จาก FB page → ไม่เข้าใจ logic → ไม่รู้จะ cut ตอนไหน
**Safeguard**: ใช้ระบบตัวเองเท่านั้น ที่เข้าใจ logic ทุกขั้นตอน
**System rule**: SR Sniper = Dream's system. เข้าใจทุก step ก่อน trade.

## Rules (Built Into System)

| Rule | Implementation |
|------|----------------|
| ห้าม revenge trade | Cooldown 16 candles |
| ต้องยืนยัน level | Confluence score + wick sweep |
| Fixed risk % | Lot calculator formula |
| ห้ามขยับ SL | SL set once at entry |
| XAUUSD only | System only scans one asset |
| ห้าม Martingale | No lot increase logic exists |
| ใช้ระบบตัวเอง | SR Sniper logic only |
| ห้ามเข้าทันที | Wait for candle close + confirmation |
| Session filter | London + NY only |
| Trend alignment | Never counter-trend |

## Psychology Notes

- Dream ต้องการ **high win rate** → เพราะ losing streaks ทำให้เสียวินัย
- SR Sniper max consecutive losses = 1 → เหมาะกับจิตวิทยา Dream
- ยังไม่ trade เงินจริง จนกว่าจะ validate ด้วย data มากพอ (100+ trades)
- Paper trading first → build confidence → then real money (1% risk)

## Key Insight

> "การ trade จริงๆ ง่ายมาก = แนวต้านแนวรับ"
> — Dream, 2026-04-11

The system should be simple enough to trust. If it's too complex, Dream won't follow it.

**Link**: [[Key Decisions]], [[North Star]], [[Strategies]]
