# claude-code-for-PMs

Strategic PM assistant for Pau Navarro, Senior Product Manager at Rakuten TV Enterprise (WLA). Built on Claude Code with a structured skill system, self-improving knowledge base, and output generation pipeline.

## How it works

| Layer | Folder | Written by | Agent behaviour |
|---|---|---|---|
| Global protocols | `CLAUDE.md` | Pau | Always loaded |
| Routing | `INDEX.md` | Pau | Loaded first on every task |
| Skills | `.claude/skills/` | Pau (`SKILL.md`, `artifact-example.md`) / Agent (`format-guardrails.md`) | Loaded on description match |
| Reference knowledge | `pm-uploaded-knowledge/` | Pau | Reads, never modifies |
| Accumulated intelligence | `ai-generated-knowledge/` | Agent | Enriches over time |
| Generated output | `output-files/` | Agent | Write only |

## Skills (12 across 4 domains)

| Domain | Skills |
|---|---|
| `product-execution` | functional-definition, user-story, acceptance-criteria, jira-task, jira-bug |
| `product-discovery` | persona, discovery-template |
| `product-strategy` | competitive-mapping, presentation, roadmap, stakeholder-translator |
| `product-gtm` | gtm-strategy |

## Setup

1. Clone this repo
2. Point Claude Code at this directory
3. Populate `pm-uploaded-knowledge/` with your product context
4. Set V= at the start of each session
