# Context source inventory

Use this table as an index of **every** place your team expects agents or humans to pull context from. Update it when you add tools, split product areas, or retire sources.

## How to use

- One row per source (doc, wiki page, dashboard, CRM view, research repository).
- Assign an **owner** who keeps it accurate enough for decisions.
- Mark **access** so agents know whether they can query directly (API, MCP, internal agent) or must ask a human to paste or export.
- For live tools, link the **compounding context artifact** where reusable interpretations live (for example `analytics-context.md`). The tool is the raw source; the artifact is where product meaning accumulates.

| ID | Name | Type (doc / analytics / support / CRM / research / other) | URL or path | Product area or scope | Owner | Access (agent-direct / human-mediated / restricted) | Compounding artifact | Brief inclusion method | Refresh cadence | Notes and caveats |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CTX-001 | Example: product strategy doc | doc | `docs/context/strategy.md` | All | [Name] | human-mediated | Same doc | Link + cite section | Monthly | |
| CTX-002 | Example: PostHog | analytics | [Link to project] | Core app | [Name] | agent-direct or human-mediated | `docs/context/analytics-context.md` | Reuse interpretation + refresh exact metric if needed | Live source; context reviewed weekly | Define key funnels; sampling may bias mobile |

## Suggested IDs by layer

You can leave IDs blank for small teams. For larger orgs, prefix helps:

- `DIR-` where we want to get to
- `NOW-` who we are now
- `OPS-` how we work
- `EVD-` evidence-only logs (often customer learnings)

## Live analytics (PostHog, GA, Amplitude, etc.)

For each analytics tool, add at least one row and capture:

- **Default project** or property ID and environment (prod vs staging).
- **Key dashboards or saved reports** that matter for bets (activation, retention, funnel, feature usage).
- **Segments** that are allowed for product decisions.
- **Known caveats** (ad blockers, logged-out traffic, bot traffic, GDPR, data delay).
- **Compounding artifact** where reusable interpretation lives, usually [`analytics-context.md`](./analytics-context.md) or a team-specific equivalent.
- **Brief inclusion method**: how agents should bring analytics into a brief without starting from scratch. Examples:
  - Reuse existing interpretation and cite it.
  - Refresh one saved dashboard value and update the interpretation.
  - Ask owner for a narrow readout when access is restricted.

Agents should prefer **current** queries over stale screenshots when your access model allows it, and must cite **tool + view + segment + date range** when citing numbers. If a bet-specific readout teaches something reusable, add it back to the compounding artifact.
