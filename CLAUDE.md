# CLAUDE.md — "How to Use AI" Wiki

A personal, compounding knowledge base about **how to use AI well** — broadly: practical
techniques, building with AI, and the tool/product landscape. It follows the "LLM wiki"
pattern: the LLM reads raw sources and incrementally builds and maintains an interlinked
markdown wiki. The human curates sources, directs emphasis, and asks questions; the LLM
does all reading, summarizing, cross-referencing, filing, and bookkeeping.

> This file is the **schema** — the rules an agent follows when ingesting, querying, or
> maintaining this wiki. It is co-evolved over time. When a convention here stops serving
> the work, update this file.

## Layers

- `raw/` — immutable source documents, one markdown file per source. **Source of truth.
  Never edit files here.**
- `wiki/` — the LLM-owned wiki (summaries, topic pages, index). The LLM creates and
  maintains everything here. The human reads it.
- `CLAUDE.md` — this file. The rules.

## Directory layout

```
KB_how_to_use_AI/
├── CLAUDE.md                 # this schema
├── raw/                      # immutable sources, one .md per source
│   └── 2026-06-18-context-engineering.md
└── wiki/
    ├── index.md              # THE catalog — every source + every topic
    ├── sources/              # one summary page per source  (created on first ingest)
    │   └── 2026-06-18-context-engineering.md
    └── topics/               # living synthesis pages        (created on first ingest)
        └── context-engineering.md
```

`wiki/sources/` and `wiki/topics/` are created the first time they're needed — keep the
tree minimal until content demands more.

## Language conventions (bilingual)

- **English** for: filenames, page titles, section headings, technical terms, tags,
  topic/page names, and frontmatter keys & values.
- **中文** for: all prose — summaries, explanations, takeaways, discussion, and the human's
  notes.
- Quotes pulled from a source keep their **original language**.
- Rationale: English keeps links and terminology stable and consistent across the wiki;
  Chinese prose is how the human thinks and reviews.

## Naming

- `kebab-case`, English — even when the source is in Chinese.
- A raw source and its summary page **share a date-prefixed slug** (`YYYY-MM-DD-slug.md`,
  date = ingest date) so they map 1:1 and sort chronologically:
  - `raw/2026-06-18-context-engineering.md` ↔ `wiki/sources/2026-06-18-context-engineering.md`
- Topic pages use the concept slug only, no date: `wiki/topics/context-engineering.md`.
- **Ingested marker:** once a source is fully integrated, append `_ingested` to its raw
  filename before the extension — `2026-06-18-context-engineering.md` →
  `2026-06-18-context-engineering_ingested.md`. A bare `.md` in `raw/` is **queued / not
  yet ingested**; `_ingested.md` is **done**. The marker lives only on the physical raw
  file — the summary page keeps the clean slug, so the 1:1 mapping is the raw slug *minus*
  the marker.

## Links

- **Relative markdown links only**: `[显示文本](../topics/context-engineering.md)`.
  Renders in VS Code, Obsidian, and GitHub alike.
- Do **not** use `[[wikilinks]]` (they don't render outside Obsidian).

## Frontmatter

Source summary page:

```yaml
---
title: "Context Engineering for AI Agents"   # original title, kept as-is
type: source
url: https://...
author: Anthropic
published: 2026-05-01
ingested: 2026-06-18
topics: [context-engineering, agentic-workflows]
tags: [technique]
---
```

Topic page:

```yaml
---
title: Context Engineering
type: topic
status: living
updated: 2026-06-18
sources: [2026-06-18-context-engineering]
related: [agentic-workflows, prompt-caching]
---
```

## Page types

### Source summary — `wiki/sources/<YYYY-MM-DD-slug>.md`

Faithfully captures one source. English headings, 中文 prose.

```markdown
## TL;DR
2–4 句中文，概括这篇来源讲了什么。

## Key points
- 中文要点，按重要性排列。

## Notable quotes
> 原文引用（保留原语言），可选。

## Connections
与哪些 topic / 其他 source 相关，给出链接，并用中文说明关系。

## Emphasis & notes
来自摄入前讨论：人类希望强调的角度、用途、保留意见。中文。
```

### Topic page — `wiki/topics/<concept>.md`

A **living** synthesis across sources. **Update in place** when new sources arrive — don't
just append. When new data contradicts or supersedes an old claim, say so and date it.

```markdown
## Summary
中文综述：关于这个主题，目前我们知道什么。

## Details
中文展开，关键处用行内引用链接回具体 source。

## Contradictions & open questions
来源之间的冲突、被新证据推翻的旧说法（标注日期）、尚未解决的问题。中文。

## Sources
- [Title](../sources/2026-06-18-context-engineering.md)

## Related
- [Agentic Workflows](agentic-workflows.md)
```

### Index — `wiki/index.md`

The catalog. Updated on **every** ingest. Two sections:

- `## Topics` — every topic page, with a one-line 中文 description.
- `## Sources` — every source, **newest first**:
  `YYYY-MM-DD · [Title](sources/<slug>.md) · author · 一句话中文 · [raw](../raw/<slug>_ingested.md)`

## Operations

### Ingest (one source at a time)

1. **Receive** a source: a URL, a path to a `.md`, or pasted text.
2. **Acquire into `raw/`**:
   - URL → fetch and convert to clean markdown (drop nav/ads/boilerplate; keep headings,
     body text, code, tables). Capture url / author / publish date for the summary's
     frontmatter.
   - File or paste → save into `raw/` under the naming convention. If the human already
     placed a file in `raw/`, use it as-is.
3. **Discuss before writing (mandatory).** Read the raw source, then give the human a short
   **中文** rundown of the key takeaways and ask **what to emphasize** — which angle
   matters, intended use, which existing topics it connects to. **Write nothing under
   `wiki/` until aligned.**
4. **Integrate**: write the `wiki/sources/` summary; create or update the relevant
   `wiki/topics/` pages (synthesis, cross-links, contradictions); update `wiki/index.md`
   (its `[raw]` link points to the `_ingested` filename).
5. **Mark ingested**: rename the raw file to append `_ingested` before its extension
   (`2026-06-18-context-engineering.md` → `2026-06-18-context-engineering_ingested.md`)
   so the `raw/` folder shows at a glance what's done.
6. **Report** exactly which pages were created or updated.

### Query

1. Read `wiki/index.md` to locate relevant pages; open and read them (and `raw/` if needed).
2. Answer in **中文** with citations linking back to topic / source / raw pages.
3. Offer to file substantial answers back as a new topic page, so explorations compound.
4. Output can take whatever form fits: markdown, comparison table, slides (Marp/pptx),
   chart, etc.

### Lint (on request)

Health-check the wiki: contradictions between pages, stale/superseded claims, orphan topics
(no inbound links), concepts mentioned but lacking their own page, missing cross-references,
and data gaps fillable via web search. Propose fixes plus new questions and sources worth
chasing.

## Taxonomy (emergent)

- Don't pre-build a rigid tree. Promote something to its own topic page only once it has
  enough material to stand alone; until then keep it as a section inside a broader topic.
- `type`: `source` | `topic`. Optional lightweight `tags` grow as needed
  (e.g. `technique`, `tool`, `model`, `agent`, `rag`, `eval`, `prompting`, `coding`,
  `writing`, `meta`).
- Keep the structure as simple as the content allows.

## Principles

- **Discuss before writing** to the wiki — every ingest, no exceptions.
- **Faithful over flashy**: cite sources, flag contradictions with dates, don't overstate.
- **Maintain, don't append**: update topic pages in place; keep `index.md` current; keep
  cross-links useful and, where it helps, bidirectional.
- **`raw/` is immutable.**
- **Keep it simple**; grow structure only when the content demands it.
