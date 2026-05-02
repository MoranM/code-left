---
name: build-technical-spec
description: Converts a bet brief into a standalone technical spec using the team’s own spec template when provided, with the Code-Left reference template as a gap check. Use when writing a technical spec, turning product intent into engineering requirements, defining user stories and acceptance criteria, updating a spec after brief or stakeholder changes, splitting a large bet into mini-specs, or reviewing spec readiness.
---

# Build technical spec

## Purpose

Translate product intent (prefer `bet-brief.md` or org equivalent; **spec-only** mode when the brief is absent) into a rigorous, standalone technical spec—often `Technical Spec.md`—that defines how the feature is built and can be implemented **without** opening the brief for implementation-critical behavior.

**Team spec template:** If the org provides a technical-spec / architecture doc template, **follow its headings and file naming** as the structure of record. Always read [`templates/pm/technical-spec-template.md`](../../../templates/pm/technical-spec-template.md) as a **gap check** so nothing critical is missing (especially standalone product contract, testable FRs, and UX-derived acceptance criteria).

The spec must carry enough **bet context** in `## Context from the bet` (or the org’s equivalent section title) that implementers understand why the work matters—not only what to type.

## When to apply

- After the bet is ready for implementation planning, or when the team explicitly needs an implementation-ready spec.
- Write or create a technical spec
- Turn a bet brief into a spec
- User stories, acceptance criteria, or functional requirements for a feature
- Brief changed or stakeholder comments arrived — **update** the existing spec
- Mini-spec for one piece of a split bet
- Review the spec for engineering readiness

## Required inputs

- **`bet-brief.md`** or **org product brief / PRD** for the feature _(strongly preferred — supplies UX complexity / equivalent and product guardrails)_
- If no brief: existing technical spec file or explicit product intent _(spec-only mode)_ — flag gaps with `[NEEDS CLARIFICATION]`.
- **Org technical spec template** (path or link) when the team has one—the **primary** outline to use when drafting.
- Reference / gap-check: [`templates/pm/technical-spec-template.md`](../../../templates/pm/technical-spec-template.md)

If neither brief, spec, nor minimal intent exists, stop and ask for one of: brief excerpt, spec outline, or short bullet intent.

## Guardrails (mandatory)

- Do **not** invent requirements, metrics, or constraints.
- Missing info: `[NEEDS CLARIFICATION: reason]` and list in **Remaining clarifications (non-blocking)** only if non-blocking.
- Only include assumptions when the user explicitly asks; label them.
- Prefer **concrete** repo naming when implementing in a real codebase: file paths, routes, modules, services. If you are drafting in the abstract, still be concrete about **interfaces and contracts**, not vague prose.
- The spec must be **standalone for implementation**. Do not rely on "see brief" for behavior that QA could disagree on.
- Separate **requirements** from **recommendations**:
  - Requirement = blocking contract for build/QA.
  - Recommendation = replaceable approach without changing product behavior.

## Placeholder convention (mandatory)

For unknown implementation-critical identifiers use:

- `[FLAG: <slug>]`
- `[CONFIG: <key>]`
- `[EVENT: <name>]`
- `[ROUTE: <path>]`
- `[MODEL: <name>]`
- `[FILE: <path>]`

Avoid raw `{placeholder}` values.

## Standalone product contract (mandatory)

Every technical spec must include near the top **a normative contract block**—use the org’s title if they already have one, or:

- `## Standalone product contract (v1)` (or equivalent)

Normative bullets must cover, when relevant:

- Scope ownership (which surface owns CRUD/edit flows)
- Feature flag / cutover semantics
- Primary entities and binding rules
- Ordering and default selection behavior
- Migration expectations (shape, idempotency, dedupe)
- API scope contracts (including compatibility windows)
- Requirement vs recommendation distinction
- Explicit v1 non-goals

## Workflow

0. **Bet complexity (for non-trivial work):** Follow [`../assess-work-item-complexity/SKILL.md`](../assess-work-item-complexity/SKILL.md) and [`../assess-work-item-complexity/eng-complexity-rubric.md`](../assess-work-item-complexity/eng-complexity-rubric.md). A quick chat assessment is enough for most work; produce or update `bet-complexity-assessment.md` (or the org’s equivalent) only when risk, size, disagreement, or team policy warrants a durable file. Use the brief for UX complexity when present; otherwise infer with `[INFERRED]`. Summarize routing in chat before deep spec drafting.
1. Read the **org technical spec template** if provided; always read [`templates/pm/technical-spec-template.md`](../../../templates/pm/technical-spec-template.md) and note any **gaps** the org template does not cover (add those sections or bullets rather than skipping).
2. Read `bet-brief.md` (or org brief) when present. If missing, use spec plus user context; note gaps.
3. If the brief already contains `## Spec split tracking`, treat it as authoritative — do **not** re-suggest a split.
4. Otherwise, **split suggestion (mandatory to propose; optional to adopt):** for multi-surface / multi-journey / high-risk bets, propose 3–6 mini-specs **before** writing, in this format:

```markdown
## Suggested spec split

- Spec 1 — <title>: ...
- Spec 2 — <title>: ...
- Dependencies / order: ...
- Risks: ...
```

Then ask: **single spec**, **adopt split**, or **custom split**.

5. If a technical spec file exists, read and improve it **in place** (preserve org structure); otherwise create from the org template or, absent that, from the reference template.
6. Before functional requirements, scan the repo for primary surfaces and entities involved when working in a real codebase.
7. Build the **standalone contract** first, then the rest.
8. Challenge vague inputs: failures, scale, auth, data lifecycle.
9. **User stories:** prioritized (P1, P2, P3…), independently testable where possible.
10. **Functional requirements:** derived from the brief or spec-only intent.
11. **UX translation (mandatory):** convert narrative into testable behavior, including defaults, ordering, empty/error/loading, destructive confirmations, a11y where relevant. Design files are illustrative only; **spec behavior wins**.

12. **LLM or model-assisted behavior:** if used, keep FR-LLM-001+ and mark CRITICAL. If not used, **delete** the LLM subsection entirely.
13. **Technical constraints:** thread API limits, quotas, latency, and provider caps through FRs and edge cases; mention in the intro.
14. **Extra sections when needed:** data model, analytics event list, DoD checklist, security notes.
15. **Remaining clarifications (non-blocking):** only truly non-blocking unknowns.
16. **Success criteria:** measurable and technology-agnostic where appropriate.
17. Run **standalone self-check** (below). If it fails, revise.
18. Return a summary and remaining clarifications.

## Split-spec tracking in the brief (when split adopted)

If the user adopts a split, update **`bet-brief.md` (or org brief)** with:

- `## Spec split tracking`

Each item: **Title**, **Scope (1–2 sentences)**, **Dependencies**, **Primary surfaces** (URLs/triggers), **Target spec path**.

## Mini-spec context injection (mandatory for split specs)

Include `## Context from the bet` (or `## Context from product brief` if your team keeps that title) summarizing only what this mini-spec needs: journeys, in/out of scope for this slice, non-regression constraints, surface subset.

## Iterating on an existing spec

When the brief changed or stakeholder comments arrive:

- Re-read brief and spec; apply comments to stories, FRs, edge cases, entities.
- Resolve answered `[NEEDS CLARIFICATION]` items.
- Refresh the standalone contract when decisions shift.
- Summarize deltas and remaining clarifications.

## Output quality checklist

- [ ] Each user story has priority, independent test, and Given/When/Then where applicable
- [ ] FRs are concrete and testable
- [ ] LLM section present iff LLM used
- [ ] Standalone contract exists and is authoritative
- [ ] No implementation-critical behavior requires opening the brief
- [ ] Requirement vs recommendation language is consistent
- [ ] Success criteria measurable
- [ ] UX translated into AC and states
- [ ] DoD present for larger bets

## Standalone self-check (mandatory before returning)

- Can an implementer execute from this spec without the brief?
- Flag/cutover semantics explicit?
- Ownership boundaries explicit?
- Ordering and defaults explicit?
- Migration idempotency/dedupe explicit when relevant?
- API payloads and errors explicit enough?
- Destructive actions and warnings explicit?

If any answer is "no", revise.

## Optional: engineering review

When asked to review readiness: run checklist, check consistency and gaps (auth, failure paths, testability), fix small wording issues, suggest defaults for remaining clarifications with user agreement, return a short review summary.
