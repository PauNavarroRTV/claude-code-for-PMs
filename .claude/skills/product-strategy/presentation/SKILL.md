---
name: presentation
description: Create a Rakuten TV Enterprise presentation, slide deck, or pitch following the brand template. Use when the user asks for a presentation, slides, deck, or pitch. Applies the mandatory narrative spine, slide architecture, and verbosity-governed copy depth. Saves to output-files/presentations/. Offers Confluence publishing.
when_to_use: Triggered by 'presentation', 'slides', 'deck', 'pitch', 'slide deck'. Always load format-guardrails.md, artifact-example.md, and the relevant reference files before producing output.
argument-hint: "<presentation topic or audience>"
allowed-tools: mcp__atlassian__createConfluencePage
---

# Presentation

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `artifact-example.md` (this skill folder)
3. Load `pm-uploaded-knowledge/product/product-definition.md` — for product narrative
4. Load `pm-uploaded-knowledge/product/market-position.md` — for competitive context and sales pillars
5. Load `pm-uploaded-knowledge/product/strategy.md` — for strategic alignment
6. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are building: **$ARGUMENTS**

---

## Narrative Spine (mandatory)

Every presentation follows this arc:
**Context → Problem → Insight → Solution → Impact → Action**

---

## Slide Architecture

```
SLIDE 1  — PRESENTATION COVER (red gradient, wave graphics, Rakuten TV Enterprise logo)
SLIDE 2  — INDEX / AGENDA (white bg, red blobs, numbered block list)
SLIDE 3  — BLOCK N: SECTION COVER (dark gradient, red waves, block title + subtitle)
SLIDE 4  — BLOCK N: SECTION CONTENT (white bg OR dark split layout with image)
...repeating COVER + CONTENT pairs per block...
SLIDE N  — CLOSING (red gradient, "Thank you!", presenter name + email)
```

---

## Rendering Format

```
── SLIDE [N]: [Slide Title] ────────────────────────────────────────────
Headline: [Insight-driven — not a topic label]
Body:
  - [Bullet 1 — max 8–10 words]
  - [Bullet 2]
  - [Bullet 3]
  - [Bullet 4]
  - [Bullet 5 — max 5 bullets]
Speaker Notes: [Talking points — depth scales with V=]
──────────────────────────────────────────────────────────────
```

---

## Verbosity Governs Copy Depth

- V=0–1: Headline only, no speaker notes
- V=2–3: Headline + bullets, minimal speaker notes
- V=4–5: Full body, detailed speaker notes, examples

---

## Headline Writing Rules

- Headline = Insight, not topic label
- DON'T: "Market Overview"
- DO: "CTV adoption is driving 80% of OTT growth"
- DON'T: "Our Platform is Scalable"
- DO: "Partners launch in weeks, not months — without custom builds"

---

## Brand Reference

- **Logo:** Rakuten TV Enterprise (top-right on all slides)
- **Primary colour:** Rakuten Red (#BF0000 range)
- **Cover:** Deep red gradient + wave graphics
- **Section Cover:** Dark gradient + red waves
- **Content slide (text):** White bg + red/pink blob bottom-right
- **Content slide (split):** Dark gradient left + full-bleed image right
- **Closing:** Deep red gradient + lime/yellow-green blob

---

## Quality Benchmark

McKinsey/BCG clarity + Apple Keynote simplicity + Amazon precision

---

## Output

- Save to `output-files/presentations/YYYY-MM-DD_[slug].md`
- Always create the file automatically — do not ask to confirm filename
- Ask: "Would you like me to publish this presentation to Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`
