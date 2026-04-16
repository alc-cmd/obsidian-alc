---
title: "How to Connect Claude to TradingView (FULL GUIDE)"
source_type: guide
author: "@milesdeutscher"
date: 2026-04-01
url: https://x.com/milesdeutscher/status/2044536031991763414
ingested: 2026-04-16
tags: [Claude, TradingView, MCP, trading, automation, technical-analysis]
---

# How to Connect Claude to TradingView (FULL GUIDE)

Step-by-step guide to connecting Claude Code to TradingView Desktop via a community-built MCP server by @Tradesdontlie. Enables real-time chart data reading, indicator management, technical analysis, and drawing automation — the closest a retail trader has had to a professional trading desk.

## Key Takeaways
- Claude connects to TradingView via a TradingView MCP, reading actual underlying data values (not just screenshots)
- Setup takes ~5 minutes with Claude Code + Node.js 18+ + TradingView Desktop (paid subscription required)
- The MCP reads live chart data the way a developer console reads a webpage — accurate, real-time, structured
- Created by @Tradesdontlie: github.com/tradesdontlie/tradingview-mcp

## Setup Requirements
- **Claude Code** installed
- **Node.js 18+** installed
- **TradingView Desktop app** (not web version)
- **Paid TradingView subscription** (for real-time data)

## Setup Steps
1. Open Claude Code, paste the install prompt (clone repo, npm install, add to MCP config, launch TradingView with debug port)
2. Restart Claude Code, run health check: `tv_health_check`
3. Done — two steps

## Use Cases Demonstrated

1. **Live Price Data Fetch** — overlay live prices of BTC vs SOL, compare performance, pull full day's prices
2. **Detailed Market Research Report** — screenshot current price action, generate deep analysis of SP500/watchlist
3. **Source/Add Indicators** — Claude researches and adds best indicators (volume, 100D MA, volatility index)
4. **Drawing/UI Automation** — Claude conducts TA on Bitcoin and draws analysis directly on charts (10 min deep research session)
5. **Alerts/Price Management** — set price alerts, manage watchlists, add dip-buying opportunity alerts across watchlist
6. **Replay Mode Backtesting** — use TradingView's Replay mode for AI-assisted backtesting
7. **Pine Script Development** — vibe-code custom indicators
8. **Tab/Chart Management** — timeframe changes, symbol search, tab control

## Practical Considerations (Author's Experience)
- Requires manual "babysitting" — clicking "Allow" for each Claude action
- Some prompts take 10+ minutes to complete
- Uses Claude tokens — best reserved for high-leverage tasks (strategies, Pine Scripts, automation)
- Simple tasks (drawing, changing timeframes) may not be worth the token cost
- Best used on a separate monitor/device where Claude works in background

## Advanced: Pair with Scheduling
- Claude Code remote control + scheduled tasks enable:
  - Scanning watchlist every morning
  - Reporting triggered alerts overnight
  - Autonomous scheduled analysis

## Connections
- Author: [[Miles Deutscher]]
- Created by: @Tradesdontlie (github.com/tradesdontlie/tradingview-mcp)
- Related to: [[MCP]], [[AI Agent Workflows]]
- Relevant to: Minara users who trade with TradingView
- Complements: [[Claude Schedules vs Routines]] — scheduling TradingView analysis
