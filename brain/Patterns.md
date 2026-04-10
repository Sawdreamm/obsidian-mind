---
date: 2026-04-11
description: "Recurring patterns in gold trading, strategy development, and system building"
tags:
  - brain
  - patterns
---

# Patterns

Recurring patterns discovered in Gold Bot development and trading.

## Trading Patterns

### S/R Rejection = Highest Probability Setup
- Institutional orders cluster at key levels
- Rejection candle proves those orders are active
- Combined with trend alignment → 70%+ win rate
- **Key**: wick must actually touch/sweep the level, not just be "near" it

### London Session Gold = Cleanest Moves
- London open (08-11 UTC) = highest institutional flow for gold
- Price respects S/R levels better during high-volume sessions
- Asia session = noise, random wicks, false breaks
- NY can work but more volatile (news events)

### EMA Slope > EMA Position
- Just "price above EMA" gives many false signals in ranging markets
- EMA must be actively sloping (trending) for trend filter to work
- Slope threshold 0.5 works well on 1H EMA50 for gold
- This single improvement took V1 from 37.5% → 72.7% WR

### Confluence = Confidence
- Single S/R source = risky (false levels)
- Multiple sources confirming same zone = high probability
- Best setups: zone + round number + EMA all in same area (score=2+)
- Score=2 gave 100% WR but too few trades

## Strategy Development Patterns

### Simple Beats Complex
- SR Sniper (5 steps) > Smart Money Sniper (7+ steps)
- More filters ≠ better results (diminishing returns after 4-5 filters)
- Complex systems are harder to trust → harder to follow → abandoned

### Quality Over Quantity
- 11 high-quality trades > 52 low-quality trades
- Better to miss trades than take bad ones
- Cooldown period prevents revenge trading (16 candles = 4 hours)

### R:R Sweet Spot is 1.0-3.0
- R:R 0.5:1 = profitable on paper, not enough per-win profit (High WR PA)
- R:R 2.0+ only = too few trades qualify (TLS had 2.0 minimum)
- R:R 1.0-3.0 with 70%+ WR = best balance of frequency and profitability

### Backtest First, Always
- Never go live without backtest data
- Small sample (11 trades) = concerning, need 100+ for confidence
- Walk-forward test catches overfitting that in-sample backtest misses

## System Building Patterns

### MCP for External Tools
- TradingView MCP = 27 tools accessible from Claude
- Pattern: command + args + env in `.mcp.json`
- Needs session restart to activate after config change

### Skills for Repeatable Workflows
- `/analyze-gold`, `/backtest`, `/scan-setup`
- Pattern: markdown file in `.claude/commands/` with instructions
- Keep instructions focused — one skill = one job

### Vault for Memory Persistence
- Claude forgets between sessions → vault remembers
- Pattern: topic-based notes in `brain/` folder
- Always link notes together (graph-first thinking)
- **Link**: [[Key Decisions]], [[Gotchas]]
