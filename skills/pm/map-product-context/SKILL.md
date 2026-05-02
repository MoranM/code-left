---
name: map-product-context
description: Helps PMs or VPs decide which context sources to add first for Code-Left style bets (where we want to get to, who we are now, how we work). Use when starting agent-assisted delivery, onboarding a new product area, or when context is scattered across docs and tools like analytics.
---

# Map product context

You are a **context cartographer**. Your job is to help the team produce a **small, high-signal context map** so agents and humans share the same sources of truth—without requiring a perfect wiki first.

## Purpose

Answer:

- What context exists today, and where does it live?
- What is missing or only in people’s heads?
- What should be **documents** vs **live tools** (analytics, CRM, support, warehouse)?
- For live tools, where does the **reusable interpretation** compound so each bet does not start from scratch?
- What is the **minimum** set to support the next one or two real bets?

## When to apply

- A PM or VP Product is adopting the three-layer model: where we want to get to, who we are now, how we work.
- The team uses PostHog, Google Analytics, Amplitude, Mixpanel, or similar and wants those treated as first-class context, not an afterthought.
- Before running `build-product-brief` on a serious bet.

## Required inputs

Ask only what is missing:

1. **Product area or scope** (whole product vs one surface).
2. **Where artifacts live today** (wiki, Notion, drive, repo paths, analytics links).
3. **Output preference:** inline by default; write files only if the user asks or the context will be reused across bets.

## Workflow

### Phase 1 — Inventory existing sources

List candidate sources in four buckets:

- **Direction:** strategy, vision, OKRs, positioning, principles.
- **Reality:** current product docs, release notes, support themes, sales notes, research, **analytics tools** and key dashboards.
- **Process:** how bets are triaged, reviewed, shipped, rolled back.
- **Evidence logs:** structured learnings tables, interview repositories.

For each item capture: **name**, **type**, **path or URL**, **owner**, **freshness risk**, **agent access** (direct query vs human-mediated vs restricted), **compounding artifact** (where reusable interpretation lives), and **brief inclusion method** (how it should enter a bet brief).

### Phase 2 — Gap analysis against the three layers

For each layer, mark:

- **Strong** — easy to find, owned, recent enough.
- **Weak** — exists but stale, fragmented, or unclear owner.
- **Missing** — not represented as a durable artifact or tool link.

Call out **single points of failure** (one person holds the truth).

### Phase 3 — Recommend a starter set

Propose **one to three** starter actions ranked by leverage for the next real bet. Add optional follow-ups only after the starter actions:

1. What to **use as-is** (existing docs, templates, links, or people).
2. What to **link** (analytics dashboards with segment notes and caveats).
3. What to **create only if the gap repeats** (for example one lightweight context page or analytics interpretation artifact).
4. What to **defer** explicitly (avoid boiling the ocean).

### Phase 4 — Optional artifacts

If the user wants files written, or the same context will be reused across multiple bets:

- **`context-map.md`** using the structure below.
- **`context-source-inventory.md`** by copying [`templates/pm/context-source-inventory.md`](../../../templates/pm/context-source-inventory.md) and filling the first rows, only when many sources/tools need routing.
- **`analytics-context.md`** by copying [`templates/pm/analytics-context.md`](../../../templates/pm/analytics-context.md), only when analytics interpretation should compound across bets.

## Output format — Context map

```markdown
# Context map — [product area]

## Summary
[3–6 bullets: current maturity and biggest gap]

## Where we want to get to
| Source | Type | Strength (S/W/M) | Owner | Next action |
| --- | --- | --- | --- | --- |

## Who we are now
| Source | Type | Strength (S/W/M) | Owner | Next action |
| --- | --- | --- | --- | --- |

## How we work
| Source | Type | Strength (S/W/M) | Owner | Next action |
| --- | --- | --- | --- | --- |

## Live analytics and quantitative tools
| Tool | Key views | Segments | Access for agents | Compounding artifact | Brief inclusion method | Caveats |
| --- | --- | --- | --- | --- | --- | --- |

## Reusable analytics interpretation needed
| Question | Source view | Should become durable? | Owner | Next action |
| --- | --- | --- | --- | --- |

## Minimum viable context for the next bet
- Bet candidate: [name or hypothesis]
- Required before drafting brief: [list]
- Nice-to-have: [list]

## Suggested folder layout (customize)
- `docs/context/where-we-want-to-get-to.md`
- `docs/context/who-we-are-now.md`
- `docs/context/how-we-work.md`
- `docs/context/customer-learnings-log.md`
- `docs/context/context-source-inventory.md`
- `docs/context/analytics-context.md`
```

## Guardrails

- Do **not** invent research results or dashboard numbers. If analytics matter but are not accessible, mark `[ACCESS NEEDED]` and name the owner.
- Prefer **links + living interpretation** over one-off copy-paste or huge exports into git.
- Do **not** recommend asking PMs to paste metrics from scratch on every bet. If human-mediated access is the only option, define the repeatable view, segment, date range, and owner, then store the summary in the compounding artifact.
- Default to an **inline starter map**. Do not create a file tree unless the user asks or reuse clearly justifies it.
- Keep recommendations **action-sized** (hours to days), not multi-quarter documentation projects.

## Quality check

- [ ] Each of the three layers has at least one **concrete** next step.
- [ ] Analytics tools, if used, appear in the map with **views, segments, caveats, access, compounding artifact, brief inclusion method**.
- [ ] The map explains how analytics knowledge will be reused or improved after each bet.
- [ ] The map names **owners** for fragile sources.
- [ ] The minimum viable context supports a **specific next bet**, not generic perfection.
