---
tags: [meta, procedure]
updated: 2026-04-23
---

# How to update twitter-engagement.md

## The constraint

X blocks unauthenticated scraping. WebFetch returns 402. Logged-out browsers see "hasn't posted" even for active accounts. **Automated daily updates require authentication.**

## Three options (pick one)

### Option A — Playwright with saved session (recommended)
- Log into X once in a Playwright browser. Persist the auth cookie to a local profile directory.
- Daily script opens that profile, scrapes profile + recent post metrics, appends to `twitter-engagement.md`.
- **Pros:** fully automated after one-time login. Free.
- **Cons:** re-login needed if X invalidates the session (~weeks). Technically against ToS if ever productized; fine for personal tracking.

### Option B — X Analytics CSV export
- Daily, download the CSV from https://analytics.x.com → Account overview → Export data.
- Drop it in `raw/x-analytics/` — Claude parses and appends.
- **Pros:** official data source, impression counts included.
- **Cons:** requires manual download each day.

### Option C — X API v2 (paid)
- Subscribe to Basic tier ($100/mo) or Free (read-only, severely rate-limited).
- Script hits `/2/users/:id/tweets` with metrics expansion.
- **Pros:** clean, reliable.
- **Cons:** cost or rate limits.

## Recommended flow for Option A

1. One-time: `npx playwright codegen x.com` → log in → save storage state to `~/.config/x-tracker/storage.json`.
2. Daily job (cron or Claude scheduled task at 09:00):
   - Launch Playwright with that storage state.
   - Navigate to `x.com/AlexAiSurfer`.
   - Scrape: profile stats + last 20 posts with their metrics (likes, reposts, replies, views).
   - Append new row to the Daily snapshots table.
   - Update the Top posts and Weekly summary sections.
3. Commit changes to the Obsidian vault.

## What the daily update should capture

Minimum viable per post:
- post URL, post date/time, first 80 chars of text
- impressions, likes, reposts, replies, bookmarks
- engagement rate = (likes + reposts + replies + bookmarks) / impressions

At the profile level:
- follower count (delta vs yesterday)
- total posts (delta vs yesterday → how many posted today)
