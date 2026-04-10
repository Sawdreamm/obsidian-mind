---
date: 2026-04-11
description: "Pitfalls in Gold Bot development — Python issues, data limits, trading traps, and setup gotchas"
tags:
  - brain
  - gotchas
---

# Gotchas

Things that have bitten before and will bite again.

## Python & Environment

### Python 3.9 vs 3.12
- Some packages (pydantic-core) fail to build on older Python
- TradingView MCP requires Python 3.12 — use `uv sync --python 3.12`
- Always check Python version when dependency builds fail

### UV Package Manager
- Installed via `curl -LsSf https://astral.sh/uv/install.sh | sh`
- Homebrew NOT needed (wasn't installed on Dream's Mac)
- UV binary at `/Users/dream/.local/bin/uv`
- For MCP: `uv run --directory <path> python -m <module>`

### PYTHONPATH for MCP Servers
- MCP modules need explicit PYTHONPATH in `.mcp.json` env config
- Without it: `ModuleNotFoundError: No module named 'tradingview_mcp'`
- Fix: `"env": {"PYTHONPATH": "/path/to/repo/src"}`

## Data Limitations

### yfinance 15M Data = Only ~60 Days
- yfinance free tier limits 15M candle history to ~60 trading days
- Our backtest (70 days, 4544 rows) is near the maximum available
- **Impact**: 11 trades is a small sample — can't draw strong statistical conclusions
- **Fix needed**: Download longer data from alternative source or use 1H for longer tests

### GC=F vs XAUUSD
- yfinance uses GC=F (Gold Futures) not spot XAUUSD
- Slight price differences exist (futures premium)
- Acceptable for strategy development, but live trading uses spot price
- Be aware when comparing backtest results to live execution

## Trading Traps

### Look-Ahead Bias
- Never use future data in signal generation
- Common mistake: using high/low of current candle for entry when candle hasn't closed
- SR Sniper rule: entry only AFTER signal candle closes (candle_close + next candle open)

### Fib 50-61.8% is a TRAP
- From Dream's notes: "Fib 50-61.8% = กับดัก ไม่ใช่จุดเข้า"
- Price often sweeps THROUGH these levels before reversing
- Correct approach: wait for sweep + rejection candle confirmation

### Round Numbers Attract Liquidity
- $50 intervals (2300, 2350, 2400...) are real S/R
- But they also attract stop hunts — price spikes through then reverses
- That's actually our edge: sweep round number + rejection = high probability signal

### Revenge Trading After Loss
- Dream's journal 2021: "ใจร้อน เข้าเพราะอยากได้คืนจากที่เสียไป"
- Cooldown period (16 candles = 4 hours) prevents this mechanically
- Never take a trade just because the last one lost

## Setup & Config

### MCP Needs Session Restart
- After modifying `.mcp.json`, Claude Code must restart to pick up new tools
- Just saving the file isn't enough — full session restart required

### TradingView MCP Directory
- Repo at: `/Users/dream/Desktop/gold-sniper-bot/tradingview-mcp-main/`
- NOT `/Users/dream/Desktop/tradingview-mcp-main/` (was moved into project folder)
- Has 27 tools: screening, analysis, sentiment, backtesting, etc.

### Obsidian Mind Brain Files
- Template files exist with placeholder content — must READ before WRITE
- Use Edit tool (not Write) to modify existing files
- Always preserve YAML frontmatter structure

**Link**: [[Key Decisions]], [[Patterns]], [[Tools & Infrastructure]]
