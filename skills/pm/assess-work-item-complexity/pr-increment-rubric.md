# PR complexity / implementation increments

Use this rubric when estimating **how many PRs (increments)** it should take to ship an approved, implementation-ready plan—not **whether** to route work to a coding agent vs engineering (that stays on the three axes in [`SKILL.md`](./SKILL.md)).

Aligned with the wisdomcom-monorepo **assess-pr-complexity** skill (same operating rules and report shape); paths and integration-point discovery are **repo-specific** below.

## When this applies

| Situation | What to do |
| --------- | ---------- |
| **Bet + approved spec / whole-feature plan** | Produce a PR complexity subsection (increment backlog or summary) alongside the work-item assessment. |
| **User asks** how many PRs, for an increment backlog, or for the first implementation increment | Produce the full report structure (or embed it in `bet-complexity-assessment.md`). |
| **Small feature / bug fix** without a spec | Default to **one increment** with a one-line rationale unless the scenario clearly forces multiple independently landable slices. |
| **Brief only, no spec** | State **Deferred** — do not invent PR boundaries from product intent alone; list under open gaps. |

## Relationship to `assess-work-item-complexity`

- **Three axes** (UX, behavioural, engineering): **who owns execution** and **design path**.
- **PR complexity**: **how to slice delivery** once implementation detail exists. A recommendation of **Coding agent** can still be a **multi-increment** series; **Hand to eng** can still be a single PR. Treat them as orthogonal unless you document a **delivery** reason to escalate (e.g. plan needs >5 increments → recommend re-scoping).

### Optional execution hint

If the increment backlog **genuinely** requires **more than ~3** independently landable increments, or ordering/risk is brittle, mention in the assessment that **engineering workflow** may be safer for coordination—even when Eng axis is Medium rather than High. This is guidance, not an automatic matrix override.

## Discovery: canonical increment / integration labels

When the repo maintains **integration-point** recipes (e.g. `.claude/skills/integration-points/*.md`), use the **file basenames** (without `.md`) as canonical names for each increment’s **Required skills**. Discover at assessment time from the repo—**do not** rely on a fixed list from memory.

If there is no such folder, use **descriptive labels** (e.g. `api`, `schema`, `client-surface`) or leave **Required skills** scoped to narrative-only and note **N/A — no integration-point catalog**.

## Operating rules (contract)

Prefer the **fewest increments** that preserve safety and reviewability.

- **Default one increment** when work is small, tightly coupled, and fits one reviewable change.
- **Split** only when it materially improves deployability, dependency ordering, reviewability, or risk reduction.
- **Do not** invent artificial PR boundaries for minor, tightly coupled, or same-surface work.
- Each increment must be **self-contained**, **reviewable**, and **safe to land independently**.
- Every increment must be safe to land with the **feature flag OFF** (or equivalent guard). No increment may **require** removing or mutating a legacy path **solely** to ship.
- Each increment’s acceptance criteria must include: **Switching the feature flag OFF preserves current production behavior for this increment's scope.** (If your org does not use flags, replace with the equivalent rollout guardrail.)
- If schema changes appear in an increment, also include: **New columns/tables are additive-only, nullable, and existing queries are unaffected when flag is OFF** (or equivalent).
- **Cap:** Prefer **≤ ~5** increments. If more seem necessary, the plan is likely too large—say so and recommend re-scoping under gaps.

## Report structure (embed or standalone)

Use this in **`bet-complexity-assessment.md`** under `## PR complexity (implementation increments)` or return it in chat when the user asks only for PR sizing.

```markdown
## PR complexity (implementation increments)

### Summary

- **Estimated PR count:** N
- **Recommendation:** Single increment | Multi-increment series
- **Why:** [1–3 sentences]
- **First increment for this run:** `<id>` — [title]

### Increment 1 — `<id>`

- **Title:** [short PR title]
- **Goal:** [concise user-facing goal]
- **Branch hint:** `feature/<branchHint>`
- **Execution context:** [subsystems, constraints, explicit out-of-scope]
- **Required skills:** [canonical integration-point basenames if catalog exists, else N/A / descriptive]
- **Dependencies:** none | `<prior-increment-id>`, …
- **Execution plan:**
  1. …
  2. …
- **Acceptance criteria:**
  - Switching the feature flag OFF preserves current production behavior for this increment's scope.
  - _(if schema in this increment)_ New columns/tables are additive-only, nullable, and existing queries are unaffected when flag is OFF.
  - [other checks]

### Increment 2 — `<id>`

_(repeat per increment; omit if N = 1)_

### Gaps & open questions

- [Uncovered patterns, missing spec detail, or needs no integration point covers — omit if none]
```

**Consistency:** The **first increment id** named in Summary must match **Increment 1**. Order increments by dependency (no later-only deps). **Required skills** must not fabricate catalog names—gaps go under **Gaps & open questions**.

## Quality check (PR subsection)

- [ ] Estimated PR count matches the number of increment blocks
- [ ] Each increment is independently landable with flag OFF (or org equivalent)
- [ ] Mandatory acceptance line on every increment; schema line when schema changes
- [ ] No increment exists only to tear out legacy without flag-safe behavior
- [ ] Integration names match discovered files or are honestly N/A / descriptive
