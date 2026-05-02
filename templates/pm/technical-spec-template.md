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
- **Links:** bet brief, complexity assessment if any

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
