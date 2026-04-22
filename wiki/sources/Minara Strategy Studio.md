---
title: Minara Strategy Studio
type: source
author: "Minara AI (docs)"
published: 2026-04-21
clipped: 2026-04-22
source_url: "https://minara.ai/docs/features/strategy-studio"
tags: [Minara, trading, strategy, AI, backtest, product-docs, crypto]
---

# Minara Strategy Studio

Official product documentation for Minara's Strategy Studio — an AI-powered quantitative strategy platform that lets users create, backtest, optimize, and deploy trading strategies through natural language, form builder, or code import.

## Core Value Proposition

Strategy Studio meets three user archetypes at their skill level:

| User Type | Experience | Primary Flow |
|-----------|-----------|--------------|
| **Beginners** | No trading or coding | Templates, plain-language chat |
| **Traders** | Indicator-literate, non-coder | Form builder (pair / timeframe / style / indicators) |
| **Developers** | Code-capable | Import PineScript → AI converts + optimizes |

All three paths converge on the same end state: a backtested strategy ready for one-click live deployment.

## Strategy Creation Surfaces

Three co-equal entry points in the homepage chat input:

1. **Chat (natural language)** — "Create a BTC trend following strategy" or "Longs ETH when it breaks above resistance, 3% stop loss." Attachments supported: chart screenshots with markings, video explanations.
2. **Templates** — Curated cards with live backtest results; click generates a personalized version.
3. **Form Builder** — Stepwise: pair → timeframe → style → indicators → free-text addendum.
4. **Code Import** — Paste PineScript; Minara transpiles to its execution format, preserves logic, runs backtest, suggests optimizations.

## Backtest Surface

Results split into **Metrics** and **Trades** tabs.

**Metrics (always visible):** Total Return, Max Drawdown, Win Rate, Profit Factor, Sharpe Ratio. Equity curve plotted against buy-and-hold baseline. Detailed breakdown adds: Outperformance vs Buy & Hold, Expected Payoff per trade, Long vs Short performance, Sortino + Calmar ratios, consecutive wins/losses, average holding period.

**Trades tab:** per-trade row showing Side, Entry/Exit Time + Price, exit Signal (STOP_LOSS, REVERSAL, etc.), P&L %, **MAE** (Maximum Adverse Excursion — worst drawdown during trade), **MFE** (Maximum Favorable Excursion), Cumulative P&L. Users can select specific trades and send them to AI as context — e.g., "Why did these trades get stopped out so early?"

## AI Auto-Optimization Loop

- After initial backtest, AI runs up to **5 optimization rounds** trying variants
- If 5 rounds don't improve results, AI stops and produces a report of what was tried + suggested new directions
- Manual optimization always available in chat: "Reduce the drawdown", "Add a volume filter", "Improve risk:reward"

Core requirements (user's stated intent) are respected across rounds; parameters and secondary rules flex.

## Deployment Flow

1. Click **Run** → pick wallet → review risk disclosure → confirm
2. Strategy goes live; monitored in **Autopilot dashboard** (equity, open positions, trade history)
3. **Wallet isolation rule**: if wallet is running another strategy or holds open positions/orders, the previous strategy is stopped, positions market-closed, open orders cancelled

**Version protection:** edits create a new version; the running version is never affected until explicit Update. Every AI code generation creates a version snapshot; previous versions are preserved and recoverable.

## Share Card (Coming Soon)

Post-backtest **Share** button generates a read-only visual card: strategy name, PNL, drawdown, win rate, profit curve, AI summary. Viewers see performance but **not** strategy code or parameters. Acts as a conversion surface — "Create My Strategy" CTA deep-links viewers into Minara with the sharer's invite link.

## Platform Scope & Boundaries

**User-definable:**
- Entry signals (indicators, price action, volume)
- Exit signals (take profit, stop loss, trailing stop, signal-based)
- Position actions (open, add, reduce, close)

**Platform-controlled:**
- Supported pairs (major crypto on supported exchanges)
- Max leverage capped at levels that passed backtesting without liquidation

**Current limits:**
- Single-asset per strategy (no multi-asset rotation yet)
- Price + volume data only (no news, no X posts, no external signals)
- Backtests use historical candles — no partial-fill simulation, no exchange-specific behavior

## Best-Practice Tips (from docs)

1. Be specific in prompts — "BTC trend strategy using EMA crossover on 4H with 3% stop loss" beats "make me a profitable strategy"
2. Always review backtest before live deploy
3. Judge by drawdown, not just return: +50% / −40% is riskier than +30% / −10%
4. Iterate — good strategies take multiple optimization rounds
5. Be honest about your risk tolerance; AI can tune for it
6. Test the same logic across timeframes (15m vs 4H can behave very differently)
7. Watch for overfitting — use longer backtest windows for robustness

## Disclaimers (marketing-relevant)

- Historical performance ≠ future results
- All trading involves risk
- Strategy Studio is a **tool**, not financial advice
- Strategy code is **transparent** — users can view, understand, modify all logic; transparency is explicitly positioned as a feature
- User maintains full control — stop, modify, withdraw anytime

## Significance for Minara Product Positioning

- **Three entry points** lower onboarding friction across all skill levels — this is the wedge against Pine-Script-only platforms (TradingView) and code-only quant platforms (QuantConnect)
- **AI auto-optimization with bounded rounds + transparent failure report** is the differentiator against opaque "AI trading bots"
- **Version protection** + transparent code address the two biggest retail concerns (losing money mid-edit; black-box risk)
- **Share card + invite-link conversion** turns every good backtest into a user acquisition surface — a product-led growth mechanism

## Source
- Raw: `raw/Clippings/Strategy Studio  Minara AI.md`

## Related
- [[Minara]] — the product this doc describes
- [[Trading Psychology]] — Barry's thesis (emotional discipline as data) is exactly what Strategy Studio automates out of the loop
- [[Barry AI Trading System]] — parallels Barry's "30+ custom AI tools" pattern in a packaged product form
- [[Hermes Agent]] — both embody the "AI replaces emotional / cognitive load in trading" thesis from different angles
