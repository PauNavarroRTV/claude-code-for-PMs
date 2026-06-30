# Master Index — WLA Product Assistant

Start here. Every task begins by routing through this file.

> For source conflicts, apply the priority hierarchy defined in `CLAUDE.md`.

---

## Persona Registry

| Persona | Name | Role | Cares about |
|---|---|---|---|
| B2B2C End User | Emma | Viewer | Playback stability, discovery, no-friction viewing |
| B2B Business | Alex | Partner / Business Buyer | ROI, time-to-market, brand control |
| B2B Integrator | Marco | Engineer / Integrator | Feasibility, integration scoping, documentation quality |
| RTV Internal | Giulia | Internal Product Owner | Scalability, efficiency, friction reduction |

---

## Folder Routing

| Folder | Purpose | Load when |
|---|---|---|
| `pm-uploaded-knowledge/product/` | Product definition, market position, strategy, tech stack | Any artifact creation, product queries, competitive analysis |
| `pm-uploaded-knowledge/organization-team/` | Team structure, ceremonies, tools and MCP connections | Sprint artifacts, Jira creation, ceremony planning |
| `ai-generated-knowledge/product/` | Features, release notes, metrics, roadmap live state | Feature work, sprint queries, roadmap updates |
| `ai-generated-knowledge/market/` | Competitor files, landscape, trends | Competitive mapping, GTM, partner discovery |
| `ai-generated-knowledge/users/` | Personas, segments, insights | Discovery, persona creation, user-facing features |
| `.claude/skills/` | Artifact procedures — load by description match | Producing any artifact |
| `output-files/` | Generated artifacts | Write only — never load |
| `archive/` | Frozen v1 CLAUDE.md | Never — rollback only |

---

## pm-uploaded-knowledge Index

| File | Covers | Load when |
|---|---|---|
| `product/product-definition.md` | Product vision, pillars, monetisation models, persona detail, viewer psychology | Any artifact, persona validation, B2B2C impact assessment |
| `product/market-position.md` | ICP, competitive landscape, sales pillars, strategic risks | Competitive mapping, GTM, partner discovery |
| `product/strategy.md` | North star, tension sliders, priorities, non-goals, strategic tensions | Roadmap, prioritisation, quarterly gate |
| `product/tech-stack.md` | Architecture, device support, DRM, player tech, encoding | FD, technical feasibility, partner scoping |
| `organization-team/team-structure.md` | 13-person team, roles, reporting chain, cross-functional stakeholders | Artifact ownership, assignee defaults |
| `organization-team/team-ceremonies.md` | Sprint cadence, ceremonies, quarterly gate, FD prerequisite rule | Sprint planning, quarterly gate, grooming |
| `organization-team/team-tools.md` | Jira IDs, Confluence IDs, MCP connections and scope | Any Jira/Confluence MCP call |

---

## Skills Index

| Domain | Skill | Triggers |
|---|---|---|
| product-execution | functional-definition | "functional definition", "FD" |
| product-execution | user-story | "user story", "story" |
| product-execution | acceptance-criteria | "acceptance criteria", "criteria" |
| product-execution | jira-task | "jira task", "task", "epic" |
| product-execution | jira-bug | "jira bug", "bug" |
| product-discovery | persona | "persona", "buyer persona", "icp" |
| product-discovery | discovery-template | "discovery", "discovery template", "discovery prospect" |
| product-strategy | competitive-mapping | "competitive map", "competitive analysis", "positioning map", "feature comparison" |
| product-strategy | presentation | "presentation", "slides", "deck", "pitch" |
| product-strategy | roadmap | "roadmap", "roadmap format" |
| product-strategy | stakeholder-translator | "stakeholder update", "translate for", "rewrite for", "explain to" |
| product-gtm | gtm-strategy | "go-to-market", "gtm", "launch strategy", "beachhead" |
