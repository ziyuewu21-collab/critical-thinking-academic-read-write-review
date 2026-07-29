# Critical Thinking: Academic Read / Write / Review

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

**English** · [中文](README.zh-CN.md)

Four Claude Code skills that turn academic work into deliberate practice instead of outsourcing.

The design principle behind all four: **automate the drudge, protect the muscle.** Searching, formatting and hunting for a page number are chores worth eliminating. Judging evidence, forming an argument and writing prose are capabilities worth keeping — so none of these skills produce the deliverable for you.

## The pipeline

```
literature-triage → reading-companion → writing-companion → research-reviewer
   (what to read)     (read it properly)   (get it written)    (mark it like an examiner)
```

| Skill | What it does | What it refuses to do |
|---|---|---|
| **literature-triage** | Batch-searches a direction, sorts results into core / skim / skip with a reason tied to your RQ, surfaces tensions in the literature | Never declares what the research gap *is* — that judgement is yours |
| **reading-companion** | Interrogates you through a reviewer's grid, points to the exact page/section for every question, captures your answers as the note | Never summarises the paper, never pastes the passage before you've read it |
| **writing-companion** | Staged support: free-writing → structuring → tightening, so thinking and writing stop competing | Never ghostwrites a paragraph |
| **research-reviewer** | Runs four examiner passes over your draft, tags each flag by band cost | Never rewrites your text |

## Two ideas worth stealing

**Coordinates, not content.** `reading-companion` gives you the section, page and the opening words of the target sentence — never the sentence itself. Scanning a paper to find the right paragraph is drudge work; reading that paragraph and judging it is the entire point. Paste the quote in the chat and you'll read the quote instead of the paper.

**Weakest-claim direction.** Every skill pushes the same question: *what did this actually measure, and what is the least it lets me say?* Overclaiming is the most common way a good argument loses marks, and it's invisible from the inside.

## Setup

Copy the four folders into your Claude Code skills directory (`~/.claude/skills/`). Each is a single `SKILL.md`.

Paths inside the skills use placeholders — replace with your own:

- `<ACADEMIC_ROOT>/` — where your notes, feedback and outputs live
- `<WORKSPACE_ROOT>/` — your project root

Two files the skills reference and expect you to create:

- `<ACADEMIC_ROOT>/feedback/feedback-lessons-log.md` — your own marked-work history. This is what makes the coaching specific rather than generic; without it the skills still run, but they can't target your particular failure modes.
- `<ACADEMIC_ROOT>/WEAK-MODEL-MODE.md` — the degradation protocol (optional, see below).

## Degrading safely on smaller models

These skills lean on live judgement, which weaker models do badly — and the failure mode isn't doing less, it's **bluffing a judgement that sounds right and is wrong**. Each skill carries a mechanical guardrail section: rules to follow literally, weak/strong answer anchors instead of model confidence, and an instruction to park anything it can't judge rather than fake it.

## Note

These were built for one person's specific weaknesses and tuned against real marked feedback. The protocols generalise; the diagnostics won't. Swap in your own.

## License

Licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) — © 2026 Ziyue Wu.

Use them, adapt them, share them. Credit me and link back. **No commercial use** — no reselling, no bundling into a paid course or paid product — without my written permission.

**中文**：可自由使用、修改、转发。转载请署名 Ziyue Wu 并附上本仓库链接。**禁止商用** —— 不得转卖、不得打包进付费课程或付费产品，商用需事先取得书面许可。
