# Technical specification: [FEATURE NAME]

**Branch or change ID:** `[###-short-name]`  
**Created:** [DATE]  
**Status:** Draft  
**Input:** `bet-brief.md` (or your team’s bet brief filename)

This spec defines **engineering implementation**. Product intent, user outcomes, and scope live in the bet brief—not here.

---

## Context from the bet _(mandatory)_

Summarize only what implementers need so they do not infer strategy from code:

- **Bet name and one-line value hypothesis**
- **Primary users and non-goals**
- **Links:** bet brief, `bet-complexity-assessment.md` and/or `pr-complexity-assessment.md` if maintained alongside this spec

---

## Complexity routing and delivery _(mandatory for implementation agents)_

**Purpose:** Hand off *how* this work should be executed—not only *what* to build. Coding and implementation agents use this to calibrate autonomy, sequencing, design prerequisites, and rollout. Populate using [`skills/pm/assess-work-item-complexity/SKILL.md`](../../skills/pm/assess-work-item-complexity/SKILL.md) (all rubrics, including [`pr-increment-rubric.md`](../../skills/pm/assess-work-item-complexity/pr-increment-rubric.md)). Do not invent facts; use `[INFERRED]` / `[UNKNOWN]` where inputs were incomplete.

- **Durable assessments:** [paths to `bet-complexity-assessment.md` / `pr-complexity-assessment.md`, or **none — captured only in this section**]

### Execution routing (primary)

- **Primary recommendation:** Coding agent | PM self-serve | Engineering workflow | Hand to eng
- **One-line why:** [synthesis from the three axes + product risk]
- **Escalate or pause when:** [triggers]

### Work-item tier

[ Bet | Small feature | Bug fix ]

### UX complexity & design path

- **UX complexity:** Simple | Complex | N/A (UI-only) — [evidence; cite brief Section 0 or spec scenarios]
- **Nature of change:** UX-dominant | UI-dominant | Mixed — [rationale]
- **Design system coverage:** Known pattern | Partial / unsure | Unknown / net new
- **Design path recommendation:** Coding agent | Designer review | Designer + Figma | Spec skill + front-end-designer skill
- **PM / design action (before or alongside implementation):** [what must happen on the design/UX dimension]

### Behavioural change to users

- **Level:** Low | Medium | High
- **Evidence:** [habits, comms, training, support—not UI surface alone]

### Engineering complexity

- **Level:** Low | Medium | High _(final; note if intrinsic differed after integration-point escalation)_
- **Evidence:** [2–4 bullets tied to this spec]
- **Integration mapping:** [recipe file(s) from repo catalog, **None — new pattern needed**, or **N/A — no integration catalog in repo**]

### PR complexity (implementation increments)

After this document is implementation-ready, size delivery slices per [`pr-increment-rubric.md`](../../skills/pm/assess-work-item-complexity/pr-increment-rubric.md).

- **Estimated PR count:** N
- **Recommendation:** Single increment | Multi-increment series
- **Why:** [1–3 sentences — fewest safe increments]
- **First increment for this run:** `<id>` — [title]
- **Detail:** [full increment backlog from rubric template **or** link `pr-complexity-assessment.md`]
- **If not yet sliceable:** **Deferred** — [what is missing]

### Open gaps that affect execution

- [Routing, design path, eng score, or increments could change if…]

---

## Standalone product contract (v1) _(mandatory)_

Normative bullets. An implementation agent should be able to execute from this file plus the repo.

- **Scope ownership:** [which surface owns CRUD, settings, or admin flows]
- **Feature flag or rollout:** [semantics; default off if your org uses flags]
- **Primary entities and rules:** [create/update/delete, cardinality, idempotency expectations]
- **Ordering and defaults:** [selection, empty states, destructive actions]
- **API or integration contracts:** [compatibility, error contract]
- **Explicit v1 non-goals:** [what this spec will not do]
- **Requirement vs recommendation:** [how you labeled them in this doc]

---

## User scenarios and testing _(mandatory)_

### User story 1 — [title] (Priority: P1)

[Journey in plain language]

**Why this priority:** [value]

**Independent test:** [how to verify alone]

**Acceptance scenarios:**

1. **Given** [state], **When** [action], **Then** [outcome]
2. **Given** [state], **When** [action], **Then** [outcome]

---

### User story 2 — [title] (Priority: P2)

[Repeat structure]

---

### Edge cases

- [Boundary or failure scenario]

---

## Requirements _(mandatory)_

### Functional requirements

- **FR-001:** System MUST [capability]
- **FR-002:** [Continue]

Mark unknowns explicitly, for example:

- **FR-00N:** System MUST [behavior] via [NEEDS CLARIFICATION: what is unknown]

### Key entities _(include if data is involved)_

- **[Entity]:** [meaning and relationships]

### LLM or model-assisted behavior _(include only if applicable)_

If the feature uses an LLM or similar system, add critical requirements such as:

- **FR-LLM-001:** [Input scope, grounding, refusal behavior]
- **FR-LLM-002:** [Output schema, validation, logging expectations]

If the feature does **not** use an LLM, delete this subsection.

---

## Success criteria _(mandatory)_

### Measurable outcomes

- **SC-001:** [metric or observable outcome]
- **SC-002:** [metric]

---

## Definition of done _(mandatory for larger bets)_

- [ ] Tests or checks agreed for this change type
- [ ] Observability: logs, metrics, or traces as required by your playbook
- [ ] Security and privacy review if triggered by your policy
- [ ] Docs or in-product copy updated

---

## Remaining clarifications (non-blocking)

Only list items that do **not** block starting implementation.

- [NEEDS CLARIFICATION: …]
