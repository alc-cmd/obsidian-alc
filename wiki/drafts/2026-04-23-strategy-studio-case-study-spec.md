---
type: spec
date: 2026-04-23
status: draft-approved-pending-write
article_type: case-study
voice: dan-koe
target_length: 1350
tags: [spec, article-draft, minara, strategy-studio, case-study]
---

# Spec — Strategy Studio Case Study

## Title & Subtitle (locked)

> **"I Turned a 16% BTC Backtest Into 101%. Without Writing a Line of Code."**
> *Fifteen minutes. Five AI optimization rounds. One year of historical data.*

## Thesis

The scarce resource in trading was never alpha. It was iteration. Strategy Studio collapses the iteration loop — from prompt to deployable backtested strategy in fifteen minutes — and that collapse shifts what trading skill means. This article proves it with one personal run and one comparative teardown.

## Audience

- **Primary:** Retail crypto traders who have ideas but don't code. Fluent in indicators (RSI, MACD, EMA) and metrics (Sharpe, drawdown, win rate).
- **Secondary:** TradingView power users ready to defect from Pine Script.
- **Tertiary:** AI-curious builders in the "personal quant" space. Dan Koe–adjacent readers.

## Core Claim + Proof Map

| Claim | Proof |
|-------|-------|
| Iteration was the real bottleneck | Personal run: one prompt → 5 AI rounds → deployable strategy in fifteen minutes |
| The AI is a collaborator, not a black box | Round 6 got discarded with a written reason. The 37.5% drawdown was self-disclosed. |
| The effect generalizes beyond my run | TradingView comparison: ETH SMA Crossover Sharpe -3.77 → +3.02 on same logic |
| The trader's edge has shifted | Close argument: skill = hypothesis generation + judgment + knowing when to walk |

## Structural Arc (~1350 words)

| # | Beat | Words | Key content |
|---|------|-------|-------------|
| 1 | Cold open — the numbers | 60 | Drop result first. `+16.54% → +101.78%. Sharpe 0.68 → 1.27. Win rate 46.7% → 61.54%. Same idea. Different execution.` |
| 2 | The reframe | 200 | Dan Koe move. *Most traders think the bottleneck is alpha. It isn't.* Iteration cost as the real tax. Pine Script as the dying skill. |
| 3 | Act 1 — The Idea | 200 | Show literal prompt. First backtest: +16.54%, 46.7% WR, 0.68 Sharpe, PF 1.49. "Not great. Not useless." → **Screenshot A** |
| 4 | Act 2 — The Loop | 250 | Five AI rounds. What it tried: Hard Stop 2.0→1.2%, Min Entry Score 5.0→6.5, ATR Trail 2.8x→2.0x. Round 6 discarded (volume filter). *The AI told me when it stopped. That's the part I trust.* → **Screenshot B** |
| 5 | Act 3 — The Result | 150 | +101.78%, 1.27 Sharpe, 61.54% WR, PF 1.78, 13 trades. +113.20% over BTC in a window where BTC was -11.42%. AI self-disclosed the 37.5% drawdown. → **Screenshot C** |
| 6 | The bigger proof — TradingView teardown | 250 | *Think I got lucky? Look at what it does to strategies that already exist.* ETH SMA Crossover +0.56% → +368.98%, Sharpe -3.77 → 3.02. Same logic, different optimization layer. → **Screenshot D** |
| 7 | The skill shift — close | 200 | Identity move. Trader's edge changed. Not alpha. Not code. Not screen time. *It's generating hypotheses fast, judging which backtests to pursue, knowing when to walk. Most traders die with their best ideas untested. That's the tax that just got removed.* |
| 8 | Compliance footer | 40 | *Backtest results. Historical performance does not guarantee future returns. All trading involves risk. Not financial advice.* |

## Voice Guardrails (Dan Koe)

**Rules:**
- Paragraphs: 1-3 sentences max. Often one.
- No adverbs unless precision requires.
- Kill hedging: *might, perhaps, could, arguably, I think*.
- Active verbs only.
- Structural repetition for rhythm: *X is not Y. Y is Z.*
- Metaphors drawn from economics/physics/biology: tax, bottleneck, leverage, friction, asymmetry.
- Direct "you" address — 3-5 times total across the piece. Overuse dilutes.
- Numbers raw, not rounded: `+101.78%`, never "over 100%."
- Max 4 em-dashes in the piece.
- No content-marketing throat-clearing ("In this article, I'll…", "Let's dive in").
- No emojis.

**Banned phrases:**
- Revolutionary, game-changer, democratize, leverage (verb), unlock, empower
- "Literally" as intensifier
- "It's no secret that…"
- Any sentence that starts with "So,"

**Required brand terms:**
- Strategy Studio (product name, title case)
- AI optimization rounds (not iterations or cycles)
- backtest (lowercase, no hyphen)
- Sharpe Ratio (capitalize when formal; lowercase in conversational run)

## Asset Plan

Four screenshots, user-provided, placed inline. Stored in `raw/assets/strategy-studio-case-study/`.

| # | Filename | Content | Caption |
|---|----------|---------|---------|
| A | `a-landing.png` | Landing page — prompt input + templates | *The input. Six words of intent.* |
| B | `b-optimization.png` | AI optimization log — rounds 5 & 6, best version trophy, key changes | *Round 5 won. Round 6 got discarded. That's the part I trust.* |
| C | `c-results.png` | Full results panel — equity curve, +101.78%, 113.20% BTC outperform, Sharpe 1.27 | *One year of BTC. 13 trades. 61.54% hit rate.* |
| D | `d-tv-comparison.png` | TradingView-vs-Minara comparison grid — ETH SMA Crossover hero | *Same strategies. Different optimization layer.* |

## Compliance & Legal

- Disclaimer footer required: *"Backtest results. Historical performance does not guarantee future returns. All trading involves risk. Not financial advice."*
- "Backtest" must remain visible in the title — already present.
- Timeframe anchor ("one year of historical data") in subtitle.
- TradingView comparison section = competitor comparison. Frame factually, not adversarially: "the same logic, optimized" — not "TradingView is broken."
- No superlatives in body copy.
- No claims about live/realized performance. All numbers are backtest numbers.

## File Layout

| Artifact | Path |
|----------|------|
| Spec (this file) | `wiki/drafts/2026-04-23-strategy-studio-case-study-spec.md` |
| Final article | `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` |
| Screenshot assets | `raw/assets/strategy-studio-case-study/{a,b,c,d}.png` |

## Open Questions (resolve before draft write)

1. **Actual prompt text** — Screenshots show the resulting strategy ("Quant Trend Long") but not the original prompt Alex typed. Caption A assumes "Six words of intent" — if the real prompt was longer, caption and Act 1 change. Alex to provide verbatim prompt, or confirm a representative phrasing.
2. **Distribution channel** — Medium? LinkedIn long-form? Minara blog? X longform? Each may need a trimmed variant (Twitter thread = 600 words, LinkedIn = 1000, Medium/blog = full 1350).
3. **Byline/author attribution** — Alex personally, or Minara brand? Case-study first-person reads stronger as personal; brand channel reads institutional.
4. **CTA at end** — implicit (just the disclaimer), or explicit link to Strategy Studio waitlist?
5. **Minara internal review** — legal/compliance sign-off before publish, especially for the TradingView comparison section.

## Related

- Prior banger: `wiki/analyses/From Prompt Engineering to Memory Engineering.md`
- Source: `wiki/sources/Minara Strategy Studio.md`
- Source: `raw/Clippings/Strategy Studio  Minara AI.md`
