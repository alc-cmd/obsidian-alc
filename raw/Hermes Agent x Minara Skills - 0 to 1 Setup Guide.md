# Your AI Agent Forgot Everything You Taught It Yesterday. Here's the Fix.

You tell your AI to buy the dip on ETH.

It asks you which chain. You tell it. It asks your slippage tolerance. You tell it. It asks for confirmation. You confirm.

Next morning, same setup. Same questions. Same 47 seconds of hand-holding for a trade you've done 200 times.

This is what most "AI trading" actually looks like. A glorified command line that forgets you exist the moment you close the tab.

I spent three weeks setting up something different. An AI agent that remembers my risk tolerance, knows I prefer Arbitrum for gas, automatically routes perps through Hyperliquid, and — here's the part that changed everything — *writes its own trading skills based on patterns it learns from watching me trade*.

No CLAUDE.md babysitting. No copy-pasting prompt templates. No starting from scratch every session.

This is the 0-to-1 setup guide for building it.

---

## The Problem Nobody Talks About

The crypto AI space is drowning in two things: bots that can't think, and agents that can't remember.

Trading bots execute rules. They don't adapt. They don't notice that you've been sizing down after consecutive losses, or that you always take profit at 2.3x on altcoins but let ETH run longer. They don't learn that when you say "ape in" you mean 2% of portfolio, not 20%.

AI agents are smarter — but most of them have the memory of a goldfish. Every conversation starts at zero. You are a stranger to your own tool, every single time.

This is the gap.

And it's exactly where Hermes Agent and Minara Skills intersect in a way that nothing else on the market does right now.

---

## Why This Combination

Let me be direct about what each piece does, because most guides bury this under hype.

**Hermes Agent** is an open-source AI agent by Nous Research. The thing that makes it different from Claude Code, Cursor, or any other AI tool is one mechanism: a *closed-loop learning system*. After every task, it evaluates what happened, decides what's worth remembering, and writes a Skill file — a reusable playbook — automatically.

Three layers of memory. Four, if you count user modeling.

Your tenth trade is fundamentally different from your first. The agent already knows your chain preferences, position sizing habits, risk parameters, and which tokens you track. It learned all of this by watching you.

**Minara Skills** is the financial brain. It's what gives any AI agent the ability to actually interact with markets — spot trading, perpetual futures, limit orders, wallet management, on-chain analytics, whale flow monitoring, portfolio tracking, and an AI autopilot mode for perps.

19+ chains: Ethereum, Base, Arbitrum, Optimism, Polygon, Avalanche, Solana, BSC, Berachain, Blast, Manta, Mode, Sonic, Monad, Polymarket, Hyperliquid — and more coming.

v3.0.2 scored 88/100 on crypto-skill-bench. 91 on safety. 66 passed, 10 partial, zero failed out of 76 scenarios.

Alone, Hermes is a brilliant agent with no market access. Alone, Minara Skills is a powerful trading toolkit with no learning capacity.

Together, you get an AI CFO that evolves.

---

## The Setup (From Zero)

Everything below assumes you have a Mac or Linux machine and 30 minutes. If you're on Windows, install WSL2 first.

### Step 1: Install Hermes Agent

One command:

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```

This handles Python 3.11, Node.js v22, ripgrep, ffmpeg — all of it. No dependency hell.

### Step 2: Configure Your Model Provider

Edit `~/.hermes/config.yaml`:

```yaml
model:
  provider: openrouter
  api_key: sk-or-your-key-here
  model: anthropic/claude-sonnet-4
terminal: local
```

Why OpenRouter? Flexibility. You can switch models mid-session without reconfiguring. Start with Claude Sonnet for quality. Drop to DeepSeek for bulk research. Use Gemini Flash for background tasks. One config file, infinite routing.

Cost: roughly $5-10/month in API calls for moderate use.

### Step 3: Install Minara Skills

```bash
curl -fsSL https://raw.githubusercontent.com/Minara-AI/skills/main/scripts/hermes-minara-skill-setup.sh | bash
```

One script. It installs the Minara CLI, deploys skill files to `~/.hermes/skills/minara`, and kicks off the login flow. Three-tier fallback built in — if one source fails, it tries the next. No API keys stored in plaintext.

Already on Claude Code instead? Swap the script:

```bash
curl -fsSL https://raw.githubusercontent.com/Minara-AI/skills/main/scripts/claudecode-minara-skill-setup.sh | bash
```

Verify it worked:

```bash
ls ~/.hermes/skills/minara
```

You should see the full skill suite: spot trading, perps, limit orders, wallet management, market intelligence, AI autopilot.

### Step 4: Connect Your Wallet

Launch Hermes and run your first command:

```
Login to Minara
```

Natural language. The agent walks you through wallet connection — supports MetaMask, Phantom, or Minara's built-in wallet with deposit address generation.

Fund it with USDC on any supported chain. You're live.

From this point, everything is natural language:

| What you say | What happens |
|---|---|
| "Buy 100 USDC worth of ETH" | Spot buy, routed to your preferred chain |
| "Swap 0.1 ETH to USDC" | Instant swap, best route |
| "Long ETH perp, 5x leverage" | Opens leveraged position on Hyperliquid |
| "Short BTC, 10x" | Short with leverage + stop loss (if you set that rule) |
| "Buy ETH when price hits $3000" | Limit order, watches until filled |
| "What tokens are trending?" | Real-time trending scan |
| "Analyze ETH — long or short?" | AI-generated directional analysis |
| "Show my crypto portfolio" | Full portfolio view across all chains |
| "Enable AI autopilot for perps" | Autonomous position management |

No syntax to memorize. No dashboards to click through. Just say what you want.

### Step 5: Configure MCP for Real-Time Data

This is optional but powerful. Add market data sources to your config:

```yaml
mcp_servers:
  minara:
    command: npx
    args: ["-y", "@minara/mcp-server@latest"]
    tools:
      include: [get_price, get_trending, get_whale_flows, get_portfolio]
```

Now Hermes can pull live data without you asking. Whale moves. Trending tokens. Portfolio updates. All through MCP, all with proper tool isolation.

### Step 6: Set Your Risk Parameters

This is the most important step. Tell Hermes your rules *once*:

```
My trading rules:
- Never risk more than 2% of portfolio per trade
- Default to Arbitrum for EVM trades, Solana for memecoins
- Perps max leverage: 5x
- Always set a stop loss
- Require my confirmation for any trade over $500
```

Hermes writes this into its memory system. You will never need to repeat it.

After a few sessions, it will start noticing your *implicit* patterns too — the ones you didn't explicitly state. That's the learning loop doing its work.

---

## What Happens After Setup

This is where most guides end. But the real value starts here.

**Week 1:** You're teaching. Asking for trades, confirming parameters, correcting when it gets the chain wrong. The agent is building its Skill library from your behavior.

**Week 2:** The agent starts anticipating. It suggests trades based on your tracked tokens. It routes to the correct chain without asking. It sizes positions using your established pattern, not some default.

**Week 3 and beyond:** You're delegating. "Scan for high-volume altcoins on Arbitrum under $1B market cap that are trending in whale flows." The agent runs the research, presents options, and pre-formats the trade — ready for your single confirmation.

The tenth interaction is not the same as the first. That's the entire point.

---

## The VPS Play (Optional, Powerful)

If you want 24/7 monitoring — alerts, automated research, portfolio tracking while you sleep — deploy to a VPS.

Hetzner CX22: $4/month. Memory usage under 500MB when not running local models.

Connect a Telegram or Discord gateway, and Hermes becomes a trading co-pilot that lives in your pocket. Message it from your phone. Get whale alerts. Ask for portfolio status. Execute trades. All through a chat interface you already use.

```yaml
gateways:
  telegram:
    token: your-bot-token
    allowed_users: [your-telegram-id]
```

Single gateway process. All conversations managed. This is not a notification bot — it's your full agent, accessible anywhere.

---

## What This Means for How You Trade

Most people interact with crypto markets in one of two ways.

The first: staring at charts for 16 hours, burning attention on noise, making emotional decisions at 2 AM because a candle moved 3%.

The second: setting up a dumb bot with rigid rules, watching it fail the moment market conditions shift, and going back to method one.

There's a third way. An agent that learns how *you* trade — not how some tutorial says you should trade — and compounds that knowledge over time. That handles the execution, the research, the monitoring, while you focus on the one thing that actually matters: deciding *what* to trade and *why*.

The "what" and "why" stay human. The "how" and "when" get automated by something that actually remembers your answer.

That's what this setup builds.

---

## Quick Reference

| Component | What It Does | Cost |
|-----------|-------------|------|
| Hermes Agent | Self-improving AI agent with memory + learning loop | Free (MIT) |
| Minara Skills v3 | Trading, wallet, analytics across 19+ chains + Hyperliquid perps | Free tier available |
| OpenRouter | Model routing (Claude, DeepSeek, Gemini) | ~$5-10/mo |
| VPS (optional) | 24/7 agent + Telegram/Discord access | ~$4/mo |
| **Total** | **Self-evolving AI trading agent** | **~$10-15/mo** |

---

*Setup time: 30 minutes. Compound time: every session after that.*
