---
name: competitive-mapping
description: Produce a competitive analysis for WLA in one of two output modes: (1) 2-axis quadrant map per strategic dimension, or (2) feature comparison matrix. Use when the user asks for competitive analysis, competitive mapping, positioning map, quadrant map, feature comparison, or competitor comparison. Always queries live Confluence competitor list before producing output. Updates ai-generated-knowledge/market/. Offers Confluence publishing.
when_to_use: Triggered by 'competitive map', 'competitive analysis', 'competitive mapping', 'positioning map', 'quadrant map', 'feature comparison', 'competitor comparison', '2-axis'. Always load format-guardrails.md and market-position.md before producing output.
argument-hint: "[quadrant|matrix] <dimension or feature area>"
allowed-tools: mcp__atlassian__searchConfluenceUsingCql mcp__atlassian__createConfluencePage mcp__atlassian__getConfluencePage
---

# Competitive Mapping

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `pm-uploaded-knowledge/product/market-position.md` — for WLA positioning and existing competitor intel
3. Load `pm-uploaded-knowledge/organization-team/team-tools.md` — for Confluence IDs
4. **Query live Confluence competitor list** — space `WLA`, ancestor page ID `4897570912`
5. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are producing: **$ARGUMENTS**

---

## Mode Selection

If $ARGUMENTS starts with `quadrant` or mentions positioning/dimensions → use **Mode 1: 2-Axis Quadrant Map**
If $ARGUMENTS starts with `matrix` or mentions features/capabilities → use **Mode 2: Feature Comparison Matrix**
If unclear, ask: "Do you want a positioning map (2-axis quadrant) or a feature comparison table?"

---

## Mode 1 — 2-Axis Quadrant Map

One map per strategic dimension.

```
Dimension: [e.g. Branding & Device Support]
Goal: [What winning looks like in this dimension]

X-axis: [Left label → Right label]
Y-axis: [Bottom label → Top label]

Quadrant Placement:
| Quadrant | Competitors | Insights | How to Beat Them |
|---|---|---|---|
| Top-Right | [names] | [strengths] | [WLA counter-strategy] |
| Top-Left  | [names] | [strengths] | [WLA counter-strategy] |
| Bottom-Right | [names] | [strengths] | [WLA counter-strategy] |
| Bottom-Left  | [names] | [strengths] | [WLA counter-strategy] |

Key Insight: [1–2 sentence strategic takeaway]
```

**Standard WLA dimensions:**
- Branding & Device Support
- Monetization & Ads
- Integration & Authentication
- Discovery & Personalization

Close with WLA's unified positioning statement.

---

## Mode 2 — Feature Comparison Matrix

```
Dimension: [Feature area being compared]
Goal: [What this comparison informs — FD scoping / partner RFP / roadmap gap]

| Feature | WLA | [Competitor A] | [Competitor B] | [Competitor C] |
|---|---|---|---|---|
| [Feature 1] | ✅ / ⚠️ / ❌ | ... | ... | ... |

Legend: ✅ Supported natively | ⚠️ Partial / configurable | ❌ Not supported

WLA Gaps: [Features where WLA is ⚠️ or ❌ — input for roadmap or FD]
WLA Advantages: [Features where WLA leads — input for sales / positioning]
Strategic Recommendation: [What this analysis implies for product or GTM]
```

Use `pm-uploaded-knowledge/product/market-position.md` as the authoritative source for WLA feature claims.

---

## Post-Creation

- Update `ai-generated-knowledge/market/landscape.md` with any new positioning insights
- Update `ai-generated-knowledge/market/competitors/` with per-competitor files if new intel surfaced
- Save to `output-files/competitive-maps/YYYY-MM-DD_competitive-[dimension-slug].md`
- Ask: "Would you like me to publish this competitive analysis to Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`

---

## MCP Usage

- `mcp__atlassian__searchConfluenceUsingCql` — query competitor list from Confluence (ancestor ID `4897570912`)
- `mcp__atlassian__createConfluencePage` — publish output
- Connection details in `pm-uploaded-knowledge/organization-team/team-tools.md`
