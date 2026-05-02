---
name: build-product-brief
description: Builds and improves bet briefs (product intent for a feature-sized bet) using three context layers—where we want to get to, who we are now, how we work—and the team’s own brief/PRD template when provided, or the Code-Left reference bet-brief template as a gap check. Use when creating a product brief, shaping a bet before a technical spec, or reviewing missing product sections.
---

# Build product brief (bet brief)

## Purpose

Create concise, product-focused **bet briefs** that define intent, user outcome, and scope before implementation. Every addition is a **bet** on customer value; the brief makes that hypothesis explicit. Prefer the **team’s existing brief, PRD, or product template** when they have one; use [`templates/pm/bet-brief-template.md`](../../../templates/pm/bet-brief-template.md) as a **reference shape** to find gaps and suggest refinements—not to replace working org conventions wholesale.

## When to apply

- Create or edit a bet brief (often `bet-brief.md`)
- Refine problem, promise, core outcome, and scope before a technical spec
- Review whether a brief is missing key sections

## Context paths (configure for your repo)

The agent needs **enough signal** from all three layers, not three polished files. For a first bet, links, rough notes, chat context, or existing org docs are acceptable. If the user does not supply paths, try these defaults; if missing, proceed with available context and mark meaningful gaps.

| Layer | Suggested path |
| --- | --- |
| Where we want to get to | `docs/context/where-we-want-to-get-to.md` |
| Who we are now | `docs/context/who-we-are-now.md` |
| How we work | `docs/context/how-we-work.md` |

Optional but valuable:

- Customer learnings log: `docs/context/customer-learnings-log.md` (or path linked from who-we-are-now)
- Context source inventory: `docs/context/context-source-inventory.md`
- Analytics context: `docs/context/analytics-context.md` (or path linked from who-we-are-now / context-source-inventory)

**Live analytics (PostHog, GA, Amplitude, Mixpanel, etc.):** do not treat analytics as a one-off copy-paste task. First find the team’s **living analytics context** (often `analytics-context.md`) and reuse its canonical views, segments, caveats, and interpretations. If the bet depends on a current number, refresh only the narrow metric needed using the available access model (MCP/API/direct tool, export, or human owner). Cite **tool + view + segment + date range** when used. If the readout teaches something reusable, add or propose an update to the analytics context artifact.

## Team template first (preferred)

If the user provides paths or pastes their org **product brief**, **PRD**, **initiative one-pager**, or **bet template**:

1. Treat that artifact and its headings as the **structure of record**.
2. Read [`templates/pm/bet-brief-template.md`](../../../templates/pm/bet-brief-template.md) in parallel and **map** Code-Left sections to theirs (by name or intent).
3. **Preserve** their section order and naming where reasonable; **suggest** new sections or bullets only when important intent evidence is missing (problem, user, scope, success, non-goals, evidence, UX complexity when relevant).
4. If their template has no **UX complexity** block equivalent, add or propose one aligned with Section 0 of the reference template (or mark `[INFERRED]` per workflow below).

## Required inputs

- **Team brief / PRD / product template** (path, link, or pasted outline) when available—the primary shape to fill or improve.
- Reference template for gap-check: [`templates/pm/bet-brief-template.md`](../../../templates/pm/bet-brief-template.md) (use when no team template exists, or always as comparison).
- Existing working brief file if editing (often `bet-brief.md`; org names vary—confirm with user).
- Enough direction, current-reality, and workflow context to make the bet honest (files, links, rough notes, or user-provided equivalents).

If missing details would change the bet’s value, scope, user, risk, or success signal, ask focused questions. Otherwise continue and mark `[UNKNOWN]` / `[NO EVIDENCE YET]` as follow-up.

## Guardrails

- **Co-create:** challenge assumptions; ask about edge cases, costs, and failure modes.
- **Focus on emotion and value:** Promise and core outcome should include how the user feels or gains confidence, not only tasks.
- **User journeys — fixed shape** when using the Code-Left reference template or when the team **adopts** that section: under **Affected user journeys**, each line must be `[the user] / [the intent] / [the action] / [the outcome]` with ` / ` separators. Use `[UNKNOWN]` for missing segments. If the team template encodes journeys differently, keep **their** format and capture the same four ideas in prose or bullets so nothing is lost.
- **Do not invent:** no fabricated facts, metrics, or constraints. Ground claims in the learnings log or other evidence; otherwise mark `[UNKNOWN]` or `[NO EVIDENCE YET]`.
- **Keep implementation out:** architecture belongs in `Technical Spec.md`.

## Workflow

1. If the user supplied a **team template**, read it first; otherwise read the reference bet brief template.
2. Read available direction, current-reality, and workflow context (files, links, rough notes, or user-supplied paths). Summarize internally how this bet supports direction, fits current reality, and follows team process.
3. Read the customer learnings log if linked or provided.
4. If the context source inventory or who-we-are-now lists analytics:
   - read the linked analytics context artifact first;
   - identify which reusable interpretation, dashboard, segment, or caveat applies to this bet;
   - only then ask for a current metric, export, or tool query if the brief needs a number that is missing or stale.
5. If a brief exists, improve it **in the team’s structure**; otherwise create from the team template or, absent that, from the reference template.
6. **Challenge and clarify** before writing dense sections: pain today, primary user, explicit non-goals.
7. **Section 0 — UX complexity:** infer from information so far using the reference template’s three criteria. Present classification and rationale for confirmation if the user is in the loop; otherwise document as `[INFERRED]` where needed. If the team template has an equivalent section, align with it.
8. Fill all core sections (per team template or reference). Weave evidence from learnings and analytics into narrative sections where your template places them—not as a dump of raw tables.
9. If helpful: add a short **Mapping / gap notes** block (optional) listing where the org template covers each Code-Left reference section, or what is missing.
10. If the bet produces a reusable analytics insight, include a **Suggested analytics context update** with the row or bullet to add.
11. Return a short summary of changes and remaining `[UNKNOWN]` items.

## Output quality checklist

- [ ] **Context used** block lists the sources actually used for direction, current reality, and workflow—or states what is still missing and whether it blocks the bet.
- [ ] Affected journeys satisfy the four-part ` / ` rule **or** the team’s equivalent format, with no dropped intent.
- [ ] **UX complexity** is captured (reference Section 0, team equivalent, or `[INFERRED]` with gaps listed).
- [ ] Clear before/after transformation under core outcome.
- [ ] Out of scope and success signals are concrete.
- [ ] If analytics sources were mapped, the brief uses a living analytics interpretation or explicitly says why analytics were not relevant.
- [ ] Any new reusable analytics learning is proposed back to the analytics context artifact.
- [ ] No engineering design in the brief.
