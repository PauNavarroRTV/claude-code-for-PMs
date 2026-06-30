---
name: roadmap
description: Create a product roadmap in the right format for the right audience. Supports 6 formats: Now/Next/Later, Hybrid, Strategic, Gantt, OKR, Dashboard. Use when the user asks for a roadmap, roadmap view, roadmap format, or roadmap update. Selects format based on audience and time horizon. Never mixes strategy and delivery in the same view. Queries live Jira sprint state.
when_to_use: Triggered by 'roadmap', 'roadmap format', 'roadmap view', 'now next later', 'gantt', 'OKR roadmap', 'strategic roadmap'. Always load format-guardrails.md and artifact-example.md before producing output.
argument-hint: "<audience or format> <context>"
allowed-tools: mcp__atlassian__searchJiraIssuesUsingJql mcp__atlassian__search mcp__atlassian__createConfluencePage
---

# Roadmap

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `artifact-example.md` (this skill folder)
3. Load `pm-uploaded-knowledge/product/strategy.md` — for current priorities and non-goals
4. Query Jira for live sprint state: `project = WLA AND sprint in openSprints() ORDER BY priority ASC`
5. Query Confluence for recently shipped: "WLA Release Notes" page in WLA space
6. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are building a roadmap for: **$ARGUMENTS**

---

## Step 1: Identify Audience and Need

Ask if not provided:
- Who is the primary audience?
- What decision does this roadmap inform?
- Do they need to plan against your dates?
- How much uncertainty exists in the scope?

---

## Step 2: Select Format

| Audience | Primary Need | Recommended Format |
|---|---|---|
| Board / CEO / Exec | Resource allocation, strategic direction | Strategic or Hybrid |
| Sales & Marketing | Revenue planning, feature availability | Hybrid or Dashboard |
| Engineering | What to build, in what order | Gantt or OKR |
| Partners / Customers | What's coming, when to expect it | Now/Next/Later or Hybrid |
| Cross-functional (all at once) | Org-wide visibility | Dashboard |

**Hard rule:** Never mix strategy and delivery.
- Time horizon > 3 months → strategy formats only (Now/Next/Later, Strategic, Hybrid)
- Time horizon ≤3 months with confirmed scope → delivery formats (Gantt, OKR, Dashboard)
- Asked to show both → produce two separate views, never one combined

---

## Format Templates

### Now / Next / Later
```
NOW                    NEXT                   LATER
─────────────────────────────────────────────────────
[Active initiative]    [Planned initiative]   [Candidate]
```
No dates. Outcomes only. Now = committed. Next = high confidence. Later = directional.

### Hybrid
```
           Q3 2026          Q4 2026          Q1 2027
─────────────────────────────────────────────────────
Theme A    [────────]  [────────────────]
Theme B               [────────]
Theme C    [───────────────────────]
```
Quarterly buckets. Rough bars. Group by theme, not team.

### Strategic
```
           Q3      Q4      Q1      Q2
──────────────────────────────────────────
Theme A    ████    ████    ██
Theme B            ██     ████    ████
Theme C                          ██
```
Theme-level only. No feature names. Aligns to WLA strategic pillars.

### Gantt
```
Feature              Owner    Week 1   Week 2   Week 3
──────────────────────────────────────────────────
[Feature]            [Team]   ████
[Feature]            [Team]            ████████
```
Only when scope is confirmed. Flag dependencies. Never for items in discovery.

### OKR
```
Objective: [Outcome statement]
Key Result              Target   W1    W2    W3    W4
──────────────────────────────────────────────────
[Metric]                [val]   [v]   [v]   [v]
Initiative              Done?   ☐     ☑     ☑
```

### Dashboard
```
Key Indicators          Baseline   Target   Today
──────────────────────────────────────────────────
Team         Backlog    In Progress   Shipped
```

---

## Step 3: Apply WLA Context

- Align initiative names to WLA's four feature pillars:
  Brand & Experience | Content Discovery & Engagement | Content Playback & Monetisation | Platform Integrations & Flexibility
- For partner-facing roadmaps: remove internal codenames, use partner-friendly language
- For exec roadmaps: every theme must connect to a revenue or retention outcome

---

## Output

- Save to `output-files/roadmaps/YYYY-MM-DD_roadmap-[format]-[audience].md`
- Update `ai-generated-knowledge/product/roadmap.md` with the current Now/Next/Later state
- Ask: "Would you like me to publish this roadmap to Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`
