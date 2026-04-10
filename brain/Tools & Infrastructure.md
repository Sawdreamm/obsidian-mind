---
date: 2026-04-11
description: "Gold Bot tooling — TradingView MCP, Vibe-Trading, RTK, MetaApi, data sources, and dev setup"
tags:
  - brain
  - tools
---

# Tools & Infrastructure

## Connected Tools

### TradingView MCP (27 tools)
**Repo**: `/Users/dream/Desktop/gold-sniper-bot/tradingview-mcp-main/`
**Config**: `.mcp.json` at project root
**Status**: Configured, needs session restart to activate
**Capabilities**:
- Market screening (scan for setups across timeframes)
- Technical analysis (indicators, patterns, S/R detection)
- Sentiment analysis (fear/greed, positioning)
- News & calendar (economic events)
- Backtesting on TradingView data

**Setup**:
```bash
uv sync --python 3.12 --directory /Users/dream/Desktop/gold-sniper-bot/tradingview-mcp-main
```
**Env required**: `PYTHONPATH=/Users/dream/Desktop/gold-sniper-bot/tradingview-mcp-main/src`

### Claude Code Skills (3 custom)
**Location**: `/Users/dream/Desktop/gold-sniper-bot/.claude/commands/`
| Skill | Purpose |
|-------|---------|
| `/analyze-gold` | Comprehensive XAUUSD analysis (TradingView MCP + SR Sniper logic) |
| `/backtest` | Run backtests with any strategy, compare results |
| `/scan-setup` | Scan for active trading setups matching SR Sniper criteria |

### Vibe-Trading (Multi-Agent Framework)
**Repo**: `/Users/dream/Desktop/gold-sniper-bot/Vibe-Trading-main/`
**Status**: Downloaded, not yet integrated
**Useful for**:
- Walk-Forward testing (train/test split to detect overfitting)
- Monte Carlo permutation test (statistical significance)
- Bootstrap Sharpe CI (confidence interval on performance)
- Multi-agent architecture patterns (68 skills)
**Integration plan**: Extract statistical validation methods for SR Sniper testing

### RTK (Token Optimizer)
**Repo**: Not yet downloaded/installed
**Purpose**: Reduce LLM token usage 60-90% for AI coding tools
**Status**: Pending installation
**Link**: https://github.com/rtk-ai/rtk.git

## Data Infrastructure

### Data Sources
| Source | Asset | Timeframes | Limitation |
|--------|-------|------------|------------|
| yfinance (GC=F) | Gold Futures | 15M, 1H, 4H | 15M = ~60 days only |
| yfinance (DX-Y.NYB) | DXY Index | 1H | Adequate |
| MetaApi (Tickmill MT5) | XAUUSD spot | All | Not yet connected for data |

### Data Files
| File | Location | Rows | Period |
|------|----------|------|--------|
| GCF_15m.csv | project root | 4544 | 2026-01-29 → 2026-04-10 |
| GCF_1h.csv | project root | 3723 | 2025-08-13 → 2026-04-10 |
| GCF_4h.csv | project root | 1011 | Resampled from 1H |
| DXYNYB_1h.csv | project root | 3868 | 2025-08-13 → 2026-04-10 |

### Data TODO
- [ ] Download longer 15M data (need >6 months for robust validation)
- [ ] Consider alternative data sources: MetaApi historical, broker data export
- [ ] Cross-validate with TradingView data via MCP

## Execution Infrastructure

### Current (Signal Only)
```
cron (15 min) → Python engine → SR Sniper scan → LINE Notify alert → Dream trades on MT5
```

### Future (Paper Trading)
```
cron → scan → alert → log trade → track P&L → dashboard
```

### Eventually (Semi-Auto)
```
MetaApi → auto-place order → manage SL/TP → alert result → Dream monitors
```

## Dev Environment

- **Machine**: Mac M4
- **Python**: 3.11+ (3.12 for TradingView MCP)
- **Package Manager**: UV (`/Users/dream/.local/bin/uv`)
- **IDE**: Claude Code (CLI)
- **Memory**: Obsidian Mind vault (this vault)
- **Broker**: Tickmill MT5
- **Alert**: LINE Notify API

## Key File Paths

```
/Users/dream/Desktop/gold-sniper-bot/          # Project root
├── strategy/sr_sniper.py                       # Primary strategy
├── .mcp.json                                   # MCP server config
├── .claude/commands/                           # Skills
├── obsidian-mind-main/brain/                   # This vault
├── tradingview-mcp-main/                       # TradingView MCP
├── Vibe-Trading-main/                          # Statistical validation
└── run_compare.py                              # Backtest comparison runner
```

**Link**: [[Key Decisions]], [[Gotchas]], [[North Star]]
