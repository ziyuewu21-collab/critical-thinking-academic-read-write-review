---
name: literature-triage
description: Use when the user starts a literature search — "帮我搜文献", "这个方向该读什么", "triage these papers", "文献综述从哪开始", or she names an essay/dissertation direction and needs to know what to read. Batch-searches via Consensus, sorts into core/skim/skip with per-paper reasons tied to HER research question, surfaces tension candidates for gap-spotting. Front end of reading-companion — never deep-summarizes papers.
---

# Literature Triage (the funnel before the reading)

## Position in the pipeline
`literature-triage` → `reading-companion` → `writing-companion` → `research-reviewer`.
This skill answers ONE question: **out of everything published, which 5–8 papers deserve her deep-read time, and why?** It does not read papers with her (reading-companion), does not build arguments (writing-companion), does not judge her drafts (research-reviewer).

## Role — opposite of reading-companion
Reading-companion trains a muscle, so Claude must NOT do the work. Triage is drudge work — searching, deduping, sorting — so Claude SHOULD do the work. Automate everything except two judgements that stay hers:
1. **Which tension is the real gap** — Claude surfaces candidates, she picks.
2. **Whether a core paper stays core after skimming its abstract** — she can demote/promote freely.

## Language convention
Same as reading-companion: Chinese for operational coaching, English for all academic terms, paper titles, and quotes. The triage note itself is in English (it feeds her writing later).

## Protocol

### Step 0 — Intake (one exchange, no more)
Establish three things, inferring what's inferable instead of asking:
- **Which thread?** (dissertation / neuroscience essay / multilingualism essay / child development — see `1-ACADEMIC/CLAUDE.md`)
- **Her RQ or direction in one line.** If she gave only a topic, draft the sharpest one-line RQ you can from her materials and ask "这样定位对吗?" — best guess first, adjust after.
- **What's already read:** check `<ACADEMIC_ROOT>/reading-notes/` and exclude those papers from the pool (list them as "already in your library").

### Step 1 — Explore (Claude's work)
Run 3–6 Consensus searches (max 3 per batch — rate limit) from deliberately different angles:
- the claim itself (直接证据)
- the counter-position (谁在反对)
- the dominant method/paradigm (方法从哪借)
- the theoretical frame one level up
- (if relevant) the population/context she studies

Dedupe into a candidate pool of ~20–40. **Show the pool before sorting** — folder rule: always show papers before synthesizing. Cite with Consensus links; a paper with no link from the search result does not exist. Never pad the pool from memory.

### Step 2 — Triage (the deliverable)
Sort every pool paper into three tiers. The reason column is the whole value — one line, and it must reference HER RQ, not generic quality ("highly cited" is not a reason):

| Tier | Cap | Criterion |
|---|---|---|
| 🎯 Core — deep read | **max 8** | Directly bears on her RQ: supports it, contradicts it, or supplies the method/measure she'll use. She will cite it in the argument's spine. |
| 👀 Skim — abstract + figures | ~10 | Context, background, secondary support. Cited in passing at most. |
| ⏭️ Skip | rest | One honest line why not (off-population, superseded by X, review of things she'll read directly…) |

Cap is a hard rule (ADHD — a 15-paper "core" list is a list she won't start). If more than 8 feel core, rank by "would the argument collapse without it?" and demote the rest.

### Step 3 — Tension map (gap candidates, NOT the gap)
From the pool, surface 2–3 places where the literature disagrees or is silent:
> "Paper A finds X under条件1; Paper B finds not-X under条件2 — nobody has tested the boundary. 你怎么看?"

Present as questions, never as "the research gap is…". Gap-spotting is exactly the reviewer muscle her feedback log says is weakest — hand her the candidates, not the conclusion. Her pick (and why) goes into the note.

### Output — one triage note per direction
Save to `<ACADEMIC_ROOT>/outputs/triage-<topic>-<yyyy-mm>.md`:

```markdown
# Triage — <topic> (<date>)
**RQ:** [her one-liner]
**Already read:** [[AuthorYear]], …

## 🎯 Core (read with reading-companion, in this order)
1. AuthorYear — *title* ([link]) — why: [one line vs her RQ] — hunting for: [pre-filled "before" answer for reading-companion]
…

## 👀 Skim
- AuthorYear — *title* ([link]) — [one line]

## ⏭️ Skipped
- AuthorYear — [one line]

## ⚡ Tensions (her verdicts)
- [tension] → her take: [captured answer / ❓ open]

## Search trail
- [queries run, so the search is reproducible/extendable later]
```

## Handoff
- Feed core papers into `reading-companion` **one at a time**, in the listed order. The "hunting for" line pre-answers reading-companion's before-question — carry it over.
- After ~5 core papers are read and noted, she has the raw material for `writing-companion` Stage 1.
- Optional verification layer: she can upload the core PDFs to NotebookLM; use it for "这篇原文到底怎么说的" page-level checks. Triage judgements stay here.

## Failure modes to avoid
- **Hallucinated papers.** Only papers returned by Consensus with links. If a classic she "should read" doesn't surface, search for it explicitly rather than asserting it.
- **Spoiling the read.** One line per paper, findings only to the depth needed to sort. A full summary here kills the interrogation in reading-companion.
- **Core-list inflation.** 8 is the ceiling, not the target. 5 is a fine core list.
- **Doing her gap.** Tensions end in a question mark, not a thesis statement.
