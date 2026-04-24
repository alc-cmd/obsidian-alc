---
type: plan
date: 2026-04-24
spec: wiki/drafts/2026-04-23-strategy-studio-case-study-spec.md
status: ready-to-execute
tags: [plan, article-draft, minara, strategy-studio]
---

# Strategy Studio Case-Study Article Implementation Plan

> **For agentic workers:** This is an article-drafting plan, not code. "Tasks" are draft sections; "tests" are voice/brand self-reviews. Commits happen automatically via Obsidian auto-backup. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Draft a ~1350-word Dan Koe–voice case-study article proving Strategy Studio turned a 16.54% BTC backtest into 101.78% in fifteen minutes, per the approved spec.

**Architecture:** Eight sections written in order (cold open → reframe → Act 1/2/3 → TradingView teardown → skill-shift close → compliance footer). After each section: self-review against Dan Koe voice rules and compliance guardrails before writing the next. Single-author continuity — no subagent dispatch (voice/rhythm degrades across agents).

**Tech Stack:** Markdown, Obsidian vault, inline screenshot embeds.

**Spec reference:** All word budgets, voice rules, banned phrases, required brand terms, and asset captions live in the spec. Do not duplicate — re-read the spec if in doubt.

---

## File Structure

| File | Role |
|------|------|
| `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` | Final article (create) |
| `raw/assets/strategy-studio-case-study/a-landing.png` | Screenshot A — landing page |
| `raw/assets/strategy-studio-case-study/b-optimization.png` | Screenshot B — optimization log |
| `raw/assets/strategy-studio-case-study/c-results.png` | Screenshot C — full results panel |
| `raw/assets/strategy-studio-case-study/d-tv-comparison.png` | Screenshot D — TradingView teardown grid |
| `wiki/drafts/2026-04-23-strategy-studio-case-study-spec.md` | Spec (read-only reference) |
| `wiki/drafts/2026-04-24-strategy-studio-case-study-plan.md` | This plan |

---

## Task 0: Resolve the Actual Prompt Text

**Blocker for Task 3 (Act 1 — The Idea). Cannot draft the first-person scene without the real prompt.**

**Files:** None yet.

- [ ] **Step 1:** Alex provides the verbatim prompt typed into Strategy Studio chat that produced "Quant Trend Long" (BTC/USDT 4h).
- [ ] **Step 2:** If Alex doesn't remember, pick the most plausible short phrasing matching Minara's documented example prompts (e.g., "Create a BTC trend following strategy") and tag as "representative, not verbatim" inside the article.
- [ ] **Step 3:** Record the prompt text at the top of Task 3 before drafting.

**Completion check:** Exact prompt text (verbatim or representative) locked in this plan.

---

## Task 1: Stage Screenshots

**Files:**
- Create dir: `raw/assets/strategy-studio-case-study/`
- Alex saves 4 image files (manual step)

- [ ] **Step 1:** Alex saves the three screenshots already shared in this session to:
  - `raw/assets/strategy-studio-case-study/c-results.png` (the Quant Trend Long full panel)
  - `raw/assets/strategy-studio-case-study/d-tv-comparison.png` (the "Turn Ideas Into Quant Strategies" landing page with TV comparison)
  - Screenshot of the `Performance + Trades Analysis` detail goes in `raw/assets/strategy-studio-case-study/c2-results-detail.png` (optional supplementary)
- [ ] **Step 2:** Alex captures two additional screenshots if needed:
  - `a-landing.png` — clean landing page with empty prompt input (or reuse d-tv-comparison.png cropped to the top if shot is already clean)
  - `b-optimization.png` — the AI optimization log panel, rounds 5 & 6 visible
- [ ] **Step 3:** Verify file names match exactly what the article's markdown will reference.

**Completion check:** `ls raw/assets/strategy-studio-case-study/` shows 4 PNG files with expected names.

---

## Task 2: Write Section 1 — Cold Open (60 words)

**Files:**
- Create: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md`

- [ ] **Step 1: Write frontmatter + title + subtitle + cold open**

```markdown
---
type: analysis
date: 2026-04-24
tags: [article, minara, strategy-studio, case-study, trading, AI, backtest]
---

# I Turned a 16% BTC Backtest Into 101%. Without Writing a Line of Code.

*Fifteen minutes. Five AI optimization rounds. One year of historical data.*

---

+16.54% → +101.78%. Sharpe 0.68 → 1.27. Win rate 46.7% → 61.54%. Profit factor 1.49 → 1.78.

Same idea. Different execution.

One year of BTC. One prompt. Fifteen minutes.
```

- [ ] **Step 2: Self-review**
  - Word count: ~55 body words after title/subtitle. Within 60-word budget.
  - Banned phrases? (none) ✓
  - Numbers raw, not rounded? ✓
  - First sentence hooks? ✓ (raw number delta)
- [ ] **Step 3:** Save. Obsidian auto-backup will commit.

**Completion check:** File exists at target path. Cold open reads punchy. Numbers correct against spec.

---

## Task 3: Write Section 2 — The Reframe (200 words)

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append)

- [ ] **Step 1: Draft**

Beat requirements (from spec):
- Dan Koe reframe: *Most traders think the bottleneck is alpha. It isn't.*
- Iteration cost was the real tax.
- Pine Script as the dying skill.
- Set up the personal run that follows.

Draft content (edit to taste, keep ~200 words):

```markdown
## The bottleneck was never your idea.

Every retail trader I know has a notebook full of setups they never tested.

*What if I trail the stop tighter on 4h BTC?*
*What if I only enter on volume spikes?*
*What if EMA crossover works better with a RSI filter?*

The ideas aren't the problem. They were never the problem.

The problem was the tax.

To test one idea, you had to learn Pine Script, or hire someone who knew it, or pay a subscription for a bot you couldn't look inside. Every variant — every "what if" — was a week of work. So you rationed. You tested the ideas you were already sure about. You never tested the weird ones.

Quants figured this out decades ago. The edge isn't alpha. It's the number of hypotheses you can kill per week.

Retail didn't have that loop. Until now.
```

- [ ] **Step 2: Self-review**
  - Word count ~200? ✓
  - Paragraphs short (1-3 sentences)? ✓
  - Banned phrases? Check: no "revolutionary", no "democratize", no "unlock", no "leverage" as verb, no "so,".
  - "You" address: count. 3-5 total across the whole piece — this section uses 4, stay aware for later sections.
  - Metaphor family: "tax," "ration," "hypotheses per week" — economics/physics ✓
- [ ] **Step 3:** Save.

**Completion check:** Reads like Dan Koe (short punches, reframe, no hedging). Transitions into personal run on last line.

---

## Task 4: Write Section 3 — Act 1: The Idea (200 words)

**Blocker:** Task 0 must resolve prompt text first.

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append)

- [ ] **Step 1: Draft**

Beat requirements (from spec):
- Narrative starts. Set scene.
- Show the literal prompt.
- First backtest result: +16.54%, 46.7% WR, 0.68 Sharpe, PF 1.49.
- "Not great. Not useless."
- Embed Screenshot A.

Draft template (fill `<<PROMPT>>` from Task 0):

```markdown
## Fifteen minutes ago.

I opened Strategy Studio. Typed this:

> <<PROMPT>>

Hit enter. It asked two clarifying questions — pair, timeframe. BTC/USDT, 4h. Done.

Forty seconds later, a backtest.

One year of BTC data. Thirteen trades. **+16.54% return. 46.7% win rate. 0.68 Sharpe. 1.49 profit factor. 13.94% max drawdown.**

Not great. Not useless.

A discretionary trader would have saved it, tweaked the stop, rerun — maybe twenty times over the next week. A Pine Script user would have spent an afternoon rewriting the logic. A quant would have asked about regime filtering.

I clicked Optimize.

![Strategy Studio — the input, six words of intent](../../raw/assets/strategy-studio-case-study/a-landing.png)
```

- [ ] **Step 2: Self-review**
  - All numbers match spec (+16.54%, 46.7%, 0.68, 1.49, 13.94%, 13 trades)? ✓
  - Asset path matches Task 1 filename? ✓
  - "Six words of intent" caption holds if prompt is short — re-tune if prompt is long.
  - Word count ~200? (draft: ~160, can expand clarifying-questions beat)
- [ ] **Step 3:** Save.

**Completion check:** Act 1 ends on the click. Next section opens on what happens after.

---

## Task 5: Write Section 4 — Act 2: The Loop (250 words)

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append)

- [ ] **Step 1: Draft**

Beat requirements (from spec):
- Five AI rounds. What it tried.
- Specific changes: Hard Stop 2.0→1.2%, Min Entry Score 5.0→6.5, ATR Trail 2.8x→2.0x.
- Round 6: volume filter, discarded.
- Trust moment: *The AI told me when it stopped.*
- Embed Screenshot B.

Draft:

```markdown
## The loop.

Strategy Studio runs up to five optimization rounds on a single click. It tries variants. Keeps what works. Discards what doesn't. Shows its work.

Here's what it did to my strategy:

- **Hard Stop** tightened from 2.0% to 1.2%. Smaller losers, more trades survive.
- **Min Entry Score** raised from 5.0 to 6.5. Fewer trades, higher conviction.
- **ATR Trail Multiplier** tightened from 2.8x to 2.0x. Locks in profits faster.

Round 5 was the winner. Sharpe up to 1.27. Return at +101.78%. Win rate at 61.54%.

Round 6 tried adding a volume filter. It didn't help.

The AI discarded it and told me why.

That last part is the part I trust.

Most AI trading products show you a number and ask you to believe. Strategy Studio showed me five attempts — three deltas that worked, one rule that didn't, and a written reason for stopping. You don't get that from a black-box bot. You don't get it from a Telegram shill. You don't get it from your own emotional iteration either, because you forget what you tried last week.

![Optimization log — round 5 wins, round 6 discarded](../../raw/assets/strategy-studio-case-study/b-optimization.png)
```

- [ ] **Step 2: Self-review**
  - Word count ~250? ✓
  - Specific numbers (2.0→1.2%, 5.0→6.5, 2.8x→2.0x) correct against spec ✓
  - "You" address count: check total across sections 1-5. Should still be under 5.
  - Banned phrases? No "game-changer," no "unlock," etc. ✓
  - Rhythm: repetition of "You don't get it from X" — Dan Koe signature ✓
- [ ] **Step 3:** Save.

**Completion check:** Trust is established. Reader sees the AI as collaborator, not oracle.

---

## Task 6: Write Section 5 — Act 3: The Result (150 words)

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append)

- [ ] **Step 1: Draft**

Beat requirements (from spec):
- Final numbers: +101.78%, 1.27 Sharpe, 61.54% WR, PF 1.78, 13 trades.
- +113.20% over BTC in a window where BTC was -11.42%.
- AI self-disclosed the 37.5% drawdown as a risk.
- Embed Screenshot C.

Draft:

```markdown
## The result.

**+101.78% total return. 1.27 Sharpe. 61.54% win rate. 1.78 profit factor. 13 trades over one year.**

BTC itself returned **-11.42%** in the same window. I outperformed the asset by **+113.20%** in a period when holding did worse than cash.

Before I get too proud, the AI told me something I didn't want to hear.

Max drawdown: 37.51%. The optimized version used 3x leverage, which amplified the winning run — and would have amplified a pullback the same way. It flagged this in plain English and offered to re-optimize at 2x leverage or target a lower drawdown.

A black-box bot doesn't do that.

![Full results — equity curve against buy-and-hold baseline](../../raw/assets/strategy-studio-case-study/c-results.png)
```

- [ ] **Step 2: Self-review**
  - Numbers correct: +101.78%, 1.27, 61.54%, 1.78, 13 trades, -11.42% BTC, +113.20% outperform, 37.51% MaxDD ✓
  - Transparency beat lands? (AI flagging drawdown = collaborator proof) ✓
  - Word count ~150? ✓
- [ ] **Step 3:** Save.

**Completion check:** Result + risk disclosure both present. No hype without qualifier.

---

## Task 7: Write Section 6 — The TradingView Teardown (250 words)

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append)

- [ ] **Step 1: Draft**

Beat requirements (from spec):
- Pivot: *Think I got lucky? Look at what it does to strategies that already exist.*
- ETH SMA Crossover: +0.56% → +368.98%, Sharpe -3.77 → 3.02.
- Other pairs as supporting data.
- Framing: same logic, different optimization layer.
- Factual, not adversarial.
- Embed Screenshot D.

Draft:

```markdown
## This isn't about one lucky run.

Strategy Studio's landing page has a section called *Browse Enhanced TradingView Strategies*. It takes public TradingView strategies, runs them through the same optimization loop I just described, and shows the before and after side by side.

The ETH 15-minute SMA Crossover Swing:

- On TradingView: **+0.56% APR. Sharpe -3.77. Win rate 39.23%.**
- After Strategy Studio's optimization: **+368.98% APR. Sharpe 3.02. Win rate 39.31%.**

Same strategy logic. The win rate barely moved. The Sharpe went from deeply negative to institutionally acceptable.

The same thing happens across the grid:

- BTC Oversold Snap-Back RSI Stochastic: Sharpe 0.48 → 2.50
- ETH Keltner Volatility Breakout: Sharpe 0.32 → 1.43
- BTC RSI Overbought Momentum Rider: Sharpe 0.23 → 0.99

Whatever the underlying logic is — trend, mean reversion, breakout, momentum — the optimization layer finds parameters the original author never got around to testing.

That's the point.

The bottleneck was never the idea. The idea was fine. What was missing was the boring, repetitive, hypothesis-killing work that nobody wants to do by hand.

![Same strategies. Different optimization layer.](../../raw/assets/strategy-studio-case-study/d-tv-comparison.png)
```

- [ ] **Step 2: Self-review**
  - Numbers match spec: +0.56%/-3.77, +368.98%/3.02, other three pairs correct ✓
  - Framing factual, not hit-piece? "The idea was fine. What was missing was the boring work" — positions TV fairly ✓
  - Word count ~250? ✓
- [ ] **Step 3:** Save.

**Completion check:** Teardown reads as factual comparison, not competitor attack. Compliance survives.

---

## Task 8: Write Section 7 — The Skill Shift Close (200 words)

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append)

- [ ] **Step 1: Draft**

Beat requirements (from spec):
- Identity shift move.
- Trader's edge changed. Not alpha. Not code. Not screen time.
- *Generate hypotheses fast. Judge which backtests to pursue. Know when to walk.*
- *Most traders die with their best ideas untested. That's the tax that just got removed.*

Draft:

```markdown
## What the trader's skill becomes.

Reading charts used to be a skill. It still is, but a shrinking one.

Writing Pine Script used to be a moat. It still is for a few people. Most of them would be better off using the fifteen minutes somewhere else.

Screen time used to correlate with edge. Now it correlates with burnout.

The edge in 2026 is three things:

1. **Generate hypotheses fast.** Every chart you look at is a potential strategy. Every indicator you half-understand is a variable. Every pattern you've doubted is a testable rule. Write them down. All of them. Especially the weird ones.
2. **Judge which backtests to pursue.** A +101% return with 37% drawdown isn't obviously better than +30% with 8%. You have to know which profile matches your capital, your holding period, your nerves.
3. **Know when to walk.** The AI told me round 6 didn't work. A discretionary trader would have tried rounds 7, 8, 9 — each one a degree further from the original thesis. Overfitting isn't a machine problem. It's a human one.

Most traders die with their best ideas untested.

That tax just got removed.
```

- [ ] **Step 2: Self-review**
  - Closing line lands? ("That tax just got removed") — callback to Section 2 ✓
  - Word count ~200? ✓
  - Identity shift clear? ✓
  - No banned phrases ✓
- [ ] **Step 3:** Save.

**Completion check:** Reader closes the tab knowing what trading skill means now.

---

## Task 9: Add Compliance Footer + Verify Full Article

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md` (append footer)

- [ ] **Step 1: Append disclaimer**

```markdown
---

*Backtest results. Historical performance does not guarantee future returns. All trading involves risk. Not financial advice.*

*Strategy Studio is a product of Minara. [Learn more →](https://minara.ai/app/trade/strategy-studio)*
```

- [ ] **Step 2:** Open the full article. Read end to end once.
- [ ] **Step 3:** Check total word count with: `wc -w "wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md"` (excluding frontmatter). Target: 1300-1500.

**Completion check:** Disclaimer present. CTA link present. Total word count within range.

---

## Task 10: Full Self-Review Pass

**Files:** No file changes. Review only.

- [ ] **Step 1: Banned-phrase scan.** Search article for each of these — none should appear:
  - `revolutionary`, `game-changer`, `democratize`, `unlock` (as "unlock value"), `empower`
  - `literally` (as intensifier)
  - `It's no secret`
  - Any sentence starting with `So,`
  - Adverbs ending in `-ly` used without precision need

- [ ] **Step 2: Required-term check.**
  - `Strategy Studio` appears ≥3x, correctly capitalized ✓
  - `backtest` lowercase, no hyphen ✓
  - `AI optimization rounds` used at least once (not "iterations") ✓

- [ ] **Step 3: Number-accuracy audit.** Cross-check every number against spec:
  - +16.54% → +101.78% ✓
  - Sharpe 0.68 → 1.27 ✓
  - WR 46.7% → 61.54% ✓
  - PF 1.49 → 1.78 ✓
  - 13 trades ✓
  - BTC return -11.42%, outperform +113.20% ✓
  - MaxDD 37.51% ✓
  - Hard Stop 2.0→1.2%, Min Entry Score 5.0→6.5, ATR Trail 2.8x→2.0x ✓
  - ETH SMA Crossover +0.56% → +368.98%, Sharpe -3.77 → 3.02 ✓

- [ ] **Step 4: Voice count.**
  - "You" direct address: 3-5 total occurrences. Count and trim if over.
  - Em-dashes: ≤4 total. Count and replace if over.
  - Paragraphs over 3 sentences: 0 acceptable. Split any that exceed.

- [ ] **Step 5: Compliance re-read.**
  - Timeframe anchor visible in subtitle ("One year of historical data") ✓
  - Disclaimer footer present ✓
  - No superlatives in body ✓
  - TV comparison framed factually, not adversarially ✓

- [ ] **Step 6:** Fix any issues inline. No need to re-review the fix.

**Completion check:** Article passes every check. Ready for Alex's review.

---

## Task 11: Present Final Article to Alex

**Files:** No changes.

- [ ] **Step 1:** Post link to final article: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md`
- [ ] **Step 2:** Surface the 4 remaining open questions from the spec (distribution channel, byline, CTA style, Minara legal review) for Alex's decision.
- [ ] **Step 3:** Await approval or revision notes.

**Completion check:** Alex responds with go/revise.

---

## Task 12 (conditional): Apply Alex's Revisions

**Files:**
- Modify: `wiki/analyses/I Turned a 16% BTC Backtest Into 101%.md`

- [ ] **Step 1:** Read Alex's feedback.
- [ ] **Step 2:** Apply edits, maintaining voice rules and word budget.
- [ ] **Step 3:** Re-run Task 10 self-review pass.
- [ ] **Step 4:** Re-present.

**Completion check:** Alex approves final version.

---

## Deviations From Standard Plan Format

This plan deviates from the writing-plans skill template because the artifact is an article, not code:

- "Tests" replaced with voice/brand/compliance self-reviews.
- Commits happen via Obsidian auto-backup (cron-based), not per-step git commits.
- No subagent dispatch — Dan Koe voice requires single-author continuity.
- Each task is a draft section with specific word budget and embedded review checks.
