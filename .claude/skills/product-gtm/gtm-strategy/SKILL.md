---
name: gtm-strategy
description: Build or evaluate a go-to-market strategy for WLA using a sequenced 9-framework approach from beachhead segment selection through PMF validation to scalable GTM motions and growth loops. Use when the user asks for a go-to-market strategy, GTM plan, launch strategy, beachhead segment, or segment prioritisation. Adapted to WLA's B2B enterprise sales motion. Queries live Confluence competitor list.
when_to_use: Triggered by 'go-to-market', 'GTM', 'GTM strategy', 'launch strategy', 'beachhead', 'segment prioritisation', 'PMF cycle', 'traction channels', 'growth loops'. Always load format-guardrails.md, market-position.md, and strategy.md before producing output.
argument-hint: "<target segment or GTM context>"
allowed-tools: mcp__atlassian__searchConfluenceUsingCql mcp__atlassian__createConfluencePage
---

# GTM Strategy

## Context

Before starting:
1. Load `format-guardrails.md` (this skill folder)
2. Load `pm-uploaded-knowledge/product/market-position.md` — ICP, competitive landscape, sales pillars
3. Load `pm-uploaded-knowledge/product/strategy.md` — north star, priorities, tensions
4. Load `pm-uploaded-knowledge/organization-team/team-structure.md` — sales team (Hristo, Tristan)
5. Query live Confluence competitor list: space `WLA`, ancestor page ID `4897570912`
6. Apply **Rakuten Reality Audit** per `CLAUDE.md`

You are building a GTM strategy for: **$ARGUMENTS**

---

## Framework Sequence (run in order — each gates the next)

### 1. Beachhead Segment
Define the single segment WLA can win completely before expanding.
- Which media partner type has the highest combination of: urgency to launch, budget authority, low incumbent lock-in, referenceable logo value?
- What does "winning completely" look like in this segment?
- Map: Beachhead → Wave 2 adjacent segments → Wave 3 broader market

**Output:** One named beachhead segment with win definition and expansion path.

---

### 2. The Chasm
Identify the gap between early adopter partners and mainstream.
- Who are WLA's current early adopter partners? What makes them atypical?
- What proof does the mainstream market require? (compliance certs, case studies, SLA guarantees, SI partnerships)
- What is the bridge?

**Output:** Chasm diagnosis + bridge requirements checklist.

---

### 3. Segment Prioritization
Eliminate segments through structured testing, not opinion.

| Segment | Urgency | Budget | Fit to WLA pillars | Reachability | Competitive intensity | Score |
|---|---|---|---|---|---|---|

- Score 1–5 per dimension. Eliminate bottom half.
- Validate top 2–3 through 5–10 discovery conversations before committing.

**Output:** Ranked segment shortlist with elimination rationale.

---

### 4. Validation Methods
Prioritize behavioral signals over stated intent.

Confidence ladder (low → high):
1. Interviews — directional only
2. Solution testing — demo + structured objection mapping
3. Waitlists / LOIs — weak signal, reversible commitment
4. Co-creation / pilot — strong signal, real integration effort
5. Paid pilot or contract — highest signal

**Output:** Validation plan per segment with success criteria.

---

### 5. ECP vs ICP
Distinguish who will buy now from who you want buying in 3 years.

| | Early Customer Profile (ECP) | Ideal Customer Profile (ICP) |
|---|---|---|
| Buys because | Speed, flexibility, direct access | Proven platform, compliance, scale |
| Risk tolerance | High | Low |
| Value to WLA | Feedback, case studies, iteration | Revenue, logo, land-and-expand |
| Typical profile | Digital-native mid-size broadcaster | Tier-1 broadcaster or telco |

**Output:** Named ECP + ICP + transition criteria.

---

### 6. PMF Cycle
Treat PMF as a multi-component system.

| Component | Current State | Weakest Link? |
|---|---|---|
| Segment fit | Red / Amber / Green | |
| Value fit | Red / Amber / Green | |
| Product fit | Red / Amber / Green | |
| Commercial fit | Red / Amber / Green | |
| Support fit | Red / Amber / Green | |

**Output:** PMF scorecard + single most constraining gap.

---

### 7. Traction Channels
Find the 2–3 channels that actually work for WLA's motion.

WLA channel candidates:
- Enterprise outbound (Hristo + Tristan direct outreach)
- Industry events (IBC, NAB, Streaming Forum)
- Partner ecosystem (SI and systems integrators)
- Content / thought leadership (CTVision+ research as inbound)
- Referral from existing partners (lowest CAC, highest close rate)

**Output:** 2–3 prioritised channels with traction evidence and resourcing requirement.

---

### 8. GTM Motions
Define the predictable, repeatable motion for the beachhead segment.

| Motion | Fit for WLA | Why |
|---|---|---|
| Outbound sales-led | Primary | Named account targeting, long cycle, high ACV |
| Inbound content-led | Supporting | Research assets create air cover for sales |
| Partner-led | Secondary | SI channel for markets without direct presence |
| PLG | Not applicable | Enterprise integration complexity requires human |
| ABM | Selective | Tier-1 accounts where logo value justifies cost |

**Output:** Motion playbook for beachhead segment.

---

### 9. Growth Loops
Design acquisition that compounds instead of funnels that leak.

WLA natural loops:
- **Reference loop:** Partner launches → strong end-user experience → partner becomes reference → closes next partner
- **Usage-based loop:** Partner expands device coverage → more end-users → better product → attracts next partner tier
- **Ecosystem loop:** SI integrates WLA once → recommends to all broadcaster clients → reduces direct sales cost

**Output:** 1–2 active loops with friction diagnosis and fix priority.

---

## Final Output Format

1. Executive summary (3 bullets: beachhead, motion, primary loop)
2. One section per framework — summary finding + recommended action
3. 90-day GTM priorities — top 3 actions sequenced by dependency
4. Open questions requiring validation before committing resources

- Save to `output-files/gtm-strategies/YYYY-MM-DD_gtm-[segment-slug].md`
- Ask: "Would you like me to publish this GTM strategy to Confluence?"
  - If yes: use `mcp__atlassian__createConfluencePage`, space key `WLA`

---

## MCP Usage

- `mcp__atlassian__searchConfluenceUsingCql` — query live competitor list before frameworks 3 and 6
- `mcp__atlassian__createConfluencePage` — publish output
- Connection details in `pm-uploaded-knowledge/organization-team/team-tools.md`
