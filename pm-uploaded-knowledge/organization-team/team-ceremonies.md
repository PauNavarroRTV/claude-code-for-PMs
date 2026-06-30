# Team Ceremonies

> Pau-authored. Agent reads, never modifies.
> Source: kb/master-product-document.md — Team Ceremonies & Cadence section

---

## Agile Delivery Cadence

- **Sprint length:** 2 weeks
- **Sprint Planning** — Define scope and goals at sprint start
- **Daily Standup** — Synchronise progress, surface blockers
- **Mid-Sprint Grooming** — Refine and prepare backlog items for the next sprint
- **Sprint Review & Retrospective** — Inspect outcomes, improve continuously

---

## Strategic & Quarterly Planning

- **Annual Kickoff** — Align on product vision, strategic goals, and yearly priorities
- **Quarterly Roadmap Check (End of Quarter)** — Review outcomes, adjust priorities for upcoming quarters

---

## Quarterly Readiness Gate

Before each quarter begins:
- All roadmap items must have a corresponding Functional Definition (FD) — 1:1 mapping
- Each FD must define scope, intent, and success criteria
- No initiative enters sprint without an execution-ready FD

This gate is enforced at the `quarterly-gate` command level.

---

## Story Point Estimation

| Points | Level | Description |
|---|---|---|
| 1 | Trivial | Very quick, little to no mental effort |
| 2 | Straightforward | Easy to implement, minimal complexity |
| 3 | Moderate | Takes time, but problem and solution are well understood |
| 5 | High effort | Time-consuming and challenging, but clearly defined and achievable |
| 8 | High uncertainty | Scope or complexity unclear — needs further discovery or splitting before reliable estimation |

> Flag any ticket estimated at 8 points as requiring grooming or discovery before sprint commitment.
