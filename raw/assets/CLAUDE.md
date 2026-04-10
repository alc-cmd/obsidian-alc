# LLM Wiki Schema

This Obsidian vault is an LLM-maintained personal knowledge base. The LLM writes and maintains all wiki content. The human curates sources, asks questions, and directs exploration.

## Directory Structure

```
raw/            # Source documents (immutable — never modify)
  assets/       # Images and attachments referenced by sources
wiki/           # LLM-generated and LLM-maintained pages
  sources/      # One summary page per ingested source
  entities/     # Pages for people, organizations, places, products
  concepts/     # Pages for ideas, frameworks, methods, themes
  analyses/     # Filed query results, comparisons, syntheses
  index.md      # Master catalog of all wiki pages
  log.md        # Chronological record of all operations
```

## Language Convention

Use the language that matches the source material. If a source is in Chinese, write its summary and related updates in Chinese. If in English, write in English. Cross-references (wikilinks) should use the canonical page name regardless of language. When a concept page aggregates sources in multiple languages, write in whichever language the majority of its sources use, or in the language the user prefers for that topic.

## Page Formats

### Source Summary (`wiki/sources/`)

```markdown
---
title: <source title>
source_type: <article | paper | book_chapter | podcast | video | report | note | other>
author: <author(s)>
date: <publication date, YYYY-MM-DD if known>
url: <original URL if applicable>
ingested: <YYYY-MM-DD>
tags: [<relevant tags>]
---

# <Source Title>

## Key Takeaways
- ...

## Summary
<2-4 paragraph summary of the source content>

## Notable Claims
- <specific claims worth tracking, with page references if applicable>

## Connections
- Related to: [[page1]], [[page2]]
- Contradicts: [[page3]] on <topic> (if applicable)
- Extends: [[page4]] (if applicable)
```

### Entity Page (`wiki/entities/`)

```markdown
---
entity_type: <person | organization | place | product | other>
aliases: [<alternative names>]
first_mentioned: <YYYY-MM-DD>
source_count: <number of sources mentioning this entity>
tags: [<relevant tags>]
---

# <Entity Name>

<Overview paragraph>

## Key Facts
- ...

## Appearances in Sources
- [[source1]] — <context>
- [[source2]] — <context>

## Related
- [[entity/concept links]]
```

### Concept Page (`wiki/concepts/`)

```markdown
---
aliases: [<alternative names>]
first_mentioned: <YYYY-MM-DD>
source_count: <number of sources discussing this concept>
tags: [<relevant tags>]
---

# <Concept Name>

<Definition and overview>

## Key Aspects
- ...

## Sources
- [[source1]] — <what it says about this concept>
- [[source2]] — <what it says about this concept>

## Open Questions
- <unresolved or contradictory points>

## Related
- [[concept/entity links]]
```

### Analysis Page (`wiki/analyses/`)

For query results, comparisons, or syntheses worth keeping.

```markdown
---
type: <comparison | synthesis | analysis | question>
date: <YYYY-MM-DD>
tags: [<relevant tags>]
---

# <Title>

<Content>

## Sources Consulted
- [[source/page links]]
```

## Workflows

### Ingest (autonomous mode)

When the user adds a source to `raw/` and asks to ingest it:

1. Read the source fully.
2. Create a summary page in `wiki/sources/`.
3. Identify entities and concepts. For each:
   - If a wiki page exists: update it with new information from this source.
   - If no page exists: create one.
4. Check for contradictions with existing wiki content. Flag them on relevant pages under "Open Questions" or "Notable Claims."
5. Update `wiki/index.md` — add new pages, update descriptions if needed.
6. Append an entry to `wiki/log.md`.
7. Report a brief summary of what was done (pages created, pages updated, contradictions found).

### Query

When the user asks a question:

1. Read `wiki/index.md` to find relevant pages.
2. Read the relevant pages.
3. Synthesize an answer with `[[wikilinks]]` to sources.
4. If the answer is substantial and reusable, offer to file it as an analysis page in `wiki/analyses/`.

### Lint

When asked to health-check the wiki:

- Look for contradictions between pages.
- Find stale claims superseded by newer sources.
- Identify orphan pages (no inbound links).
- Spot important concepts mentioned but lacking their own page.
- Find missing cross-references.
- Suggest new questions to investigate or sources to look for.

## Conventions

- Use Obsidian `[[wikilinks]]` for all internal references.
- Keep page filenames concise and descriptive. Use spaces, not hyphens. Match the title.
- Every wiki page must have YAML frontmatter.
- The index is the primary navigation tool — keep it well-organized and current.
- The log is append-only. Never edit past entries.
- Never modify files in `raw/`. That directory is the source of truth.
- When updating existing pages, preserve information from previous sources. Add to them, don't replace.
- Prefer specific pages over mega-pages. If a concept has enough content, it deserves its own page.
