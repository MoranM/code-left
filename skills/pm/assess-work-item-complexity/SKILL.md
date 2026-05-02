---
name: assess-work-item-complexity
description: Assesses work-item complexity (bets, scoped enhancements, bugs) across UX, behavioral change, and engineering complexity; recommends coding agent, PM self-serve, engineering workflow, or handoff to engineering. Accepts the team’s existing brief, spec, ticket, or notes—Code-Left templates are reference shapes for scoring, not replacements. Use before deep technical spec work, when routing a bet, or triaging small work.
---

# Assess work-item complexity

## Purpose

Produce a **routing recommendation** from three axes. Output must be **evidence-based** from available inputs—do not invent constraints, metrics, or user research.

**Org templates:** Score using whatever brief, PRD, spec, or ticket the team already uses. Use Code-Left templates ([`bet-brief-template.md`](../../../templates/pm/bet-brief-template.md), [`bet-complexity-assessment-template.md`](../../../templates/pm/bet-complexity-assessment-template.md)) as **reference** for what good evidence looks like—do **not** require rewriting their artifact into Code-Left format before routing. If their template omits UX complexity, behavioral risk, or engineering cues, **infer** with `[INFERRED]` and **suggest** additions.

Routing must reflect **product and behavior risk**, not only code size: a technically small change can still need engineering workflow if it changes trust, positioning, compliance exposure, or user mental model.

## When to apply

- Before substantial technical-spec work (especially when combined with `build-technical-spec`).
- When the user asks where a bet should land.
- When the brief lacks UX complexity (or equivalent)—infer cautiously and label `[INFERRED]`.
- For bugs or small enhancements when deciding safe autonomy.

## Work-item tiers

| Tier | Typical input | When to use |
| --- | --- | --- |
| **Bet** | Team brief/PRD, `bet-brief.md`, `Technical Spec.md`, or equivalent | Full feature or initiative |
| **Scoped enhancement** | Scenario, user story, ticket, Notion doc, or short bullets (problem, user, scope, surfaces) | Meaningful change without a full brief |
| **Bug fix** | Repro, logs, ticket | Broken behavior |

If tier is unclear, ask one question: "Is this a bug fix, a scoped enhancement, or part of a larger bet?"

## Required inputs (use what exists)

### Bet tier

1. **Product brief / PRD / `bet-brief.md`** (or your team’s filename) if present — UX complexity **or equivalent** and intent.
2. **`Technical Spec.md`** (or org spec doc) if present — engineering sizing.
3. Optional: user message, issue link, or ticket for context.

If **no brief and no spec**, ask for a brief excerpt, spec outline, ticket, or 5–10 bullets. Do not fabricate a full assessment.

### Scoped enhancement / bug tier

Scenario, repro, ticket, or short bullets are enough. Do **not** demand a full brief.

## Axis 1 — UX complexity

**Reference criteria** (when the team has no UX section): Section **0. UX complexity** in [`templates/pm/bet-brief-template.md`](../../../templates/pm/bet-brief-template.md).

- If the team brief has a filled UX / IA / scenario classification: **use it** as the source of truth.
- If missing: infer Simple vs Complex using the same three criteria; label `[INFERRED]` and list unknowns.
- If no brief: infer from spec, ticket, or scenario with `[INFERRED]`.
- Small fixes without a brief: default **Simple** unless multiple flows or IA change.

## Axis 2 — Behavioral change

Rate **Low / Medium / High** by how much users must change habits, mental model, training, comms, or support load—not UI surface alone.

| Level | Meaning |
| --- | --- |
| **Low** | Matches expectations; minimal comms. |
| **Medium** | New steps or labels; moderate help. |
| **High** | New workflow, retraining, trust or positioning shift, or high support risk. |

Small fixes: default **Low** unless user-visible behavior materially changes meaning.

## Axis 3 — Engineering complexity

Read [`eng-complexity-rubric.md`](./eng-complexity-rubric.md). Assign **Low / Medium / High** with 2–4 bullets tied to the brief or spec.

Apply the rubric’s **optional integration-point mapping** if your repo maintains integration recipes; otherwise state **N/A**.

## Routing recommendation (default matrix)

Unless the org overrides in **how we work** docs:

| Eng | UX (brief) | Behavioral | Primary recommendation |
| --- | --- | --- | --- |
| Low | Simple | Low | **Coding agent** — implement in-repo following documented standards; human reviews. |
| Low | Simple | Med/High | **Engineering workflow** — align comms, training, edge cases before build. |
| Low | Complex | any | **Engineering workflow** — design or IA validation. |
| Medium | any | Low/Med | **Engineering workflow** — standard build; PM pairs on spec and acceptance. |
| Medium | any | High | **Engineering workflow** or **hand to engineering** if rollout risk is high. |
| High | any | any | **Hand to engineering** — eng owns execution risk; PM owns intent and acceptance. |

**PM self-serve** is valid for some orgs when the change is product-owned collateral only; if **how we work** does not define it, treat PM self-serve as "engineering workflow with no code change."

**Coding agent** also implies the requester can enforce repo policies (tests, lint, typecheck, feature flags, security review triggers). If those are undefined, recommend **engineering workflow** until they exist.

**Escalation:** If the assessment depends on `[INFERRED]` or `[UNKNOWN]` for critical areas, recommend **engineering workflow** at minimum until clarified.

## Outputs

### Path A — Quick assessment (default)

Post a short assessment in chat unless the user asks for a file or the work is large/high-risk:

```markdown
## Quick complexity assessment

- **Tier:** [Bet | Scoped enhancement | Bug fix]
- **UX complexity:** [Simple | Complex] — [evidence]
- **Behavioral change:** [Low | Medium | High] — [evidence]
- **Engineering complexity:** [Low | Medium | High] — [evidence]
- **Recommendation:** [Coding agent | PM self-serve | Engineering workflow | Hand to engineering]
- **Open gaps:** [...]
```

### Path B — Full assessment file

Write **`bet-complexity-assessment.md`** next to the brief or spec (or path the user chooses) when the bet is large, high-risk, repeated, disputed, or the user wants a durable artifact. Use [`templates/pm/bet-complexity-assessment-template.md`](../../../templates/pm/bet-complexity-assessment-template.md) as the **default shape**; if the org has its own assessment section or doc, fill **that** instead and still cover the three axes with evidence.

If `bet-brief.md` or the team’s brief file exists and the user wants a summary in-product, append under their UX complexity section (or right after it):

```markdown
### Complexity routing summary

- **Recommendation:** [Coding agent | PM self-serve | Engineering workflow | Hand to engineering]
- **Detail:** See `bet-complexity-assessment.md`.
```

Skip editing the brief if the user declines.

## Guardrails

- No invented metrics or research.
- One to two pages for a written assessment.
- Bugs and small features: never require a full brief.

## Quality check

- [ ] Tier identified
- [ ] All axes scored with evidence
- [ ] Recommendation matches matrix or documents an override from **how we work**
- [ ] Open gaps listed
