---
title: "Top MCP Servers That Turn Claude Into a Productivity Machine"
source_type: article
author: "@zodchiii"
date: 2026-04-08
url: https://x.com/zodchiii/status/2041804097628582294
ingested: 2026-04-10
tags: [MCP, Claude, tools, productivity, developer-tools]
---

# Top MCP Servers That Turn Claude Into a Productivity Machine

A curated list of 35 [[MCP]] servers for Claude, tested over a year of use and sorted by category. The author filtered 10,000+ listed MCP servers down to ones that are actively maintained and solve real problems.

## Key Takeaways
- MCP (Model Context Protocol) is how Claude connects to external tools
- 3-5 servers is the recommended sweet spot — more burns tokens on tool descriptions
- Claude Code's Tool Search feature helps by lazy-loading servers
- Most of the 10,000+ listed MCP servers are unmaintained weekend projects

## Servers by Category

### Search & Research
- **Tavily** — AI-optimized web search, clean content (free: 1K queries/mo)
- **Exa** — Semantic search by meaning, not keywords (free: 1K searches/mo)
- **Brave Search** — Independent index, 6 tools (paid: from $5/mo)
- **Perplexity** — Synthesized answers with deep research (free tier)
- **Context7** — Live framework documentation, stops hallucinated APIs (free, open-source)

### Web Scraping & Data Extraction
- **Firecrawl** — URL to clean markdown, JS rendering, site crawls (free: 500 credits)
- **Apify** — 3,000+ ready-made scrapers (free: $5/mo credits)
- **Bright Data** — Heavy anti-bot bypass (paid only)
- **Crawl4AI** — Open-source crawling, best markdown extraction, 61K+ stars (free)

### Browser Automation
- **Playwright** — Claude controls real Chrome browser (free, open-source)
- **Browserbase** — Cloud-hosted browser for AI (free: 100 sessions/mo)

### Dev Tools & Code
- **GitHub** — PRs, issues, code search, CI/CD (free)
- **Linear** — Issue tracking from Claude (free tier)
- **Sentry** — Production errors with full stack traces (free: 5K errors/mo)
- **Vercel** — Deploy, build logs, error inspection (free tier)
- **Jira/Atlassian** — JQL search, sprint management (free: up to 10 users)

### Databases
- **Supabase** — Postgres + auth + storage (free tier)
- **PostgreSQL** — Natural language database queries (free, open-source)
- **MongoDB** — 40+ tools, Atlas management (free: 512MB cluster)
- **Neo4j** — Graph database, knowledge graphs (free community edition)

### Vector & AI Memory
- **Pinecone** — Cloud vector search with reranking (free: 2GB)
- **Qdrant** — Semantic memory, self-hostable (free, open-source)
- **Chroma** — Lightweight vector DB for local dev (free, open-source)
- **Memory MCP** — Knowledge graph persistent memory across sessions (free, open-source)

### Productivity & Collaboration
- **Notion** — Documents, wikis, databases (free tier)
- **Slack** — Read threads, search, send messages (free)
- **Todoist** — Task management (free tier)
- **Zapier** — 6,000+ app automation (free: 100 tasks/mo)

### Business & Finance
- **Stripe** — Payments, subscriptions, invoices (free test mode)
- **HubSpot** — CRM through Claude (free CRM)

### Design & Media
- **Figma** — Design files to code (free)
- **Bannerbear** — Automated image generation (free: 30 images/mo)

### Infrastructure & Monitoring
- **Cloudflare** — Workers, KV, D1, DNS (free tier)
- **Docker** — Container management (free, open-source)
- **Grafana** — Dashboards, metrics, alerts (free Grafana Cloud)

## Notable Claims
- Recommended starter kits by role: developers (GitHub + Sentry + Context7 + Playwright), researchers (Tavily + Firecrawl + Exa), project managers (Linear + Slack + Notion), business (Stripe + HubSpot + Zapier), data (Supabase + Firecrawl + Apify)
- All servers use the same install pattern: `claude mcp add server-name -- npx -y @package/server`

## Connections
- Related to: [[MCP]]
