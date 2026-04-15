---
title: "Claude Schedules vs Routines (What's the difference)"
source_type: article
author: "@NickSpisak_"
date: 2026-04-15
url: https://x.com/NickSpisak_/status/2044142814942961880
ingested: 2026-04-15
tags: [Claude, automation, routines, schedules, loop, developer-tools, productivity]
---

# Claude Schedules vs Routines

Claude Code has three ways to run work automatically: Routines (cloud), Desktop Schedules (local machine), and /loop (live session). Each trades off access, persistence, and setup complexity differently.

## Key Takeaways
- **Routines** = cloud-based, run even when laptop is off, but only access repo (no local files)
- **Desktop Schedules** = local, access your files/MCP servers, but machine must be on
- **/loop** = instant in-session polling, dies when terminal closes
- Most people need Routines for core workflows + /loop for everything else
- Desktop Schedules fill the gap when you need local file access on a schedule

## Routines (Cloud)

Saved configuration: prompt + GitHub repos + model + connectors (Gmail, Slack, Linear, etc.). Each run spins up a fresh cloud session.

Three trigger types:
- **Schedule** — hourly, daily, weekdays, weekly (minimum: 1 hour)
- **API** — dedicated HTTP endpoint with bearer token, callable from any external system
- **GitHub Events** — PRs, pushes, issues, releases (17 event types with filters)

Multiple triggers can stack on one routine. No local file access — every run starts from a fresh clone. Available on Pro, Max, Team, Enterprise. Currently in research preview.

## Desktop Schedules (Local)

Run against your actual working directory including uncommitted changes. Require computer on + Desktop app running.

- Frequency: manual, hourly, daily, weekdays, weekly (minimum: 1 minute)
- Permission prompts configurable — tip: use "always allow" on first Run Now test
- Missed run catch-up: runs most recent miss on wake, but only one
- Closing laptop lid stops everything; "Keep computer awake" setting prevents idle sleep only

## /loop (Session)

Session-scoped polling. Three usage patterns:
- `/loop 5m check the deploy` — fixed interval
- `/loop check the deploy` — Claude picks interval based on observations
- `/loop` — runs built-in maintenance prompt or custom `loop.md`

Expires after 7 days. Doesn't survive restarts. Can run as frequently as every minute. Survives via tmux sessions locally.

## Decision Matrix

| Factor | Routines | Desktop Schedules | /loop |
|--------|----------|-------------------|-------|
| Runs when laptop off | Yes | No | No |
| Local file access | No (fresh clone) | Yes | Yes |
| External triggers | API, GitHub events | No | No |
| Min interval | 1 hour | 1 minute | 1 minute |
| Persistence | Permanent | Permanent | Session (7d max) |
| Setup | Web UI / CLI | Desktop app | One command |
| Permissions | Fully autonomous | Configurable | Session context |

## Connections
- Related to: [[MCP]], [[AI Agent Workflows]]
- Extends: Claude Code's automation capabilities beyond manual sessions
- Complements: [[Claude Skills]] — skills define what agents do, schedules/routines define when
