---
tags: [meta, procedure]
updated: 2026-04-23
---

# How to update twitter-engagement.md

## Workflow (confirmed 2026-04-23)

**You use Option B — X Analytics CSV export.** Daily drop-in workflow:

1. **Morning (2 min manual step):**
   - Go to https://analytics.x.com → Content → Export data
   - Pick date range: **"Last 7 days"** for a daily update, or **"Last 28 days"** weekly
   - Download the CSV
2. **Drop the file:**
   - Save into `raw/x-analytics/` — keep the default filename (`account_analytics_content_YYYY-MM-DD_YYYY-MM-DD.csv`) so history is preserved
3. **Tell Claude:** "update the twitter tracker with the latest CSV"
   - Claude re-parses, updates 90-day headline, weekly trend, top-10 tables, and appends a new row to Daily snapshots
   - Flags new top performers and failed experiments

## Daily snapshot row (what Claude computes)

For each update, Claude computes deltas since the previous row:

- **Δ posts** = new posts since last check
- **Δ impressions / engagements** (period totals)
- **Δ followers** (you paste the current number — analytics.x.com → Overview)
- **Top post today** = highest-impression post dated in the new window

## Schedule

Either:

- **Self-triggered:** you drop the CSV and ping Claude when you feel like it
- **Reminder:** use the `schedule` skill to run a daily "remind me to export X analytics CSV" trigger at a fixed time

Ask if you want me to set up the reminder.

## Fallback options (if Option B gets annoying)

### Option A — Playwright with saved session
- Log into X once in a Playwright browser. Persist auth cookie.
- Daily script scrapes profile + recent post metrics, appends automatically.
- Pros: zero manual work. Cons: re-login every few weeks; fragile on X UI changes.

### Option C — X API v2
- Basic tier $100/mo. Free tier too rate-limited for this use.
- Clean and reliable, but not worth the cost at current follower scale.

## File layout

```
obsidian-alex/
├── twitter-engagement.md            ← the tracker (this is what you read)
├── twitter-engagement-howto.md      ← this file (procedure)
└── raw/
    └── x-analytics/
        └── account_analytics_content_2026-01-24_2026-04-23.csv
```

All CSVs stay in `raw/x-analytics/` — never overwrite, always append the new-dated file so you have a forensic trail.
