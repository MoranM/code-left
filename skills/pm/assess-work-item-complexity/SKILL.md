---
name: assess-work-item-complexity
description: Assesses work-item complexity (bets, small features, or bugs) across UX, user behavioural change, and engineering complexity; recommends coding agent, PM self-serve, eng workflow, or hand-off to eng. When an approved spec or whole-feature plan exists—or when the user asks for PR count or increments—also estimates implementation PRs and an ordered increment backlog (same guardrails as wisdomcom assess-pr-complexity). Accepts briefs, specs, scenarios, or repros. Works with the team’s artifacts; Code-Left templates are reference shapes—see Purpose.
---

# Assess work-item complexity (coding agent / PM self-serve / eng workflow / hand to eng)

## Purpose

Produce a **routing recommendation** for the requester based on three axes; when an implementation-ready plan exists or the user asks for delivery slicing, also address **PR complexity** via [`pr-increment-rubric.md`](./pr-increment-rubric.md). Output must be **evidence-based** from the available input—do not invent constraints or metrics.

**Org artifacts:** Score using whatever brief, PRD, spec, or ticket the team already uses. Use Code-Left templates ([`bet-brief-template.md`](../../../templates/pm/bet-brief-template.md), [`bet-complexity-assessment-template.md`](../../../templates/pm/bet-complexity-assessment-template.md)) as **reference** for Section 0-style UX complexity and assessment shape—do **not** require rewriting their artifact into Code-Left format before routing. If their template omits UX complexity, design-system coverage, behavioural risk, or engineering cues, **infer** with `[INFERRED]` and list gaps.

Routing must reflect **product and behaviour risk**, not only code size: a technically small change can still need engineering workflow if it changes trust, positioning, compliance exposure, or user mental model.

## When to apply

- **Before** substantial technical-spec work (mandatory when invoked from product-spec or `build-technical-spec` workflows).
- When the user asks where a bet should land organizationally.
- When the brief exists but Section 0 (or equivalent UX complexity) is empty—infer cautiously and mark gaps.
- When a user describes a **bug to fix** or a **small feature** and wants to know if it can be handled quickly.
- When invoked from a quick-fix-style command to decide whether to proceed or escalate.
- When the user asks **how many PRs** a plan needs, for an **increment backlog**, or which **first increment** to implement—apply [`pr-increment-rubric.md`](./pr-increment-rubric.md) in addition to the three axes (when an approved plan exists; otherwise defer PR boundaries).

## Work-item tiers

Classify the incoming request into a tier. This determines the minimum input required.

| Tier              | Typical input                                                                    | When to use                                          |
| ----------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Bet**           | Team brief / PRD, `bet-brief.md`, `Technical Spec.md`, or equivalent             | Full feature or initiative with product brief / spec |
| **Small feature** | Scenario, user story, ticket, or 3–5 bullets (problem, user, scope, surfaces)     | Scoped enhancement that doesn't warrant a full brief |
| **Bug fix**       | Repro scenario, error message / log, or ticket description                       | Something is broken and needs to be fixed            |

If the agent **cannot determine the tier** from context, ask **one** clarifying question: "Is this a bug fix, a small feature, or part of a larger bet?"

## Required inputs (use what exists)

### Bet tier

1. **Product brief / `bet-brief.md`** (or your team’s filename) if present — read Section 0 (or equivalent) for **UX complexity** and product intent.
2. **`Technical Spec.md`** or draft spec (if present) — use when the brief is missing or to size eng complexity.
3. Optional: user message, ticket link, or `$ARGUMENTS` for context.

If **no brief and no spec**, ask for one of: paste brief excerpt, paste spec outline, ticket, or 5–10 bullets (problem, user, scope, surfaces, risks). Do not fabricate a full assessment.

### Small feature / Bug fix tier

A **scenario or repro description** is sufficient. Accept any of:

- A written scenario ("When a user does X, Y should happen but Z happens instead")
- An error message or log snippet
- A short bullet list describing the desired change
- A ticket or issue description

Do **not** demand a full brief or spec for these tiers.

## Axis 1 — UX complexity and design path

This axis produces **two outputs**: a **design path classification** (UX vs UI, design system coverage, recommended PM/design action) and a **UX Simple/Complex score**.

**Before scoring:** Read [`ux-design-path-rubric.md`](./ux-design-path-rubric.md) and follow all three steps:

1. **Nature of change** — classify as `UX-dominant`, `UI-dominant`, or `Mixed`.
2. **Design system gate** — classify as `Known pattern`, `Partial / unsure`, or `Unknown / net new` using the checklist in the rubric.
3. **UX complexity (Section 0 model)** — for `UX-dominant` and `Mixed`, apply the three criteria (Scenarios / Flow impact / IA) from the brief or infer with `[INFERRED]`. For `UI-dominant`, record "N/A".

Then use the **decision table** in the rubric to determine the **design path recommendation** (Coding agent / Designer review / Designer + Figma / Spec skill + front-end-designer skill — adapt skill names to your tooling; see rubric).

**Source of truth for UX Simple/Complex:** Section **0. UX complexity** in the reference template ([`bet-brief-template.md`](../../../templates/pm/bet-brief-template.md): Scenarios / Flow impact / Information architecture → Simple vs Complex).

- If the team brief has a filled UX / IA / scenario classification: **copy the classification and rationales** into the assessment.
- If Section 0 (or equivalent) is missing or incomplete: infer **Simple vs Complex** using the same three criteria from [`bet-brief-template.md`](../../../templates/pm/bet-brief-template.md). Label as `[INFERRED]` and list what is unknown.
- If there is **no brief**: infer from the spec's user stories, surfaces, and flows with `[INFERRED]` and explicit unknowns.
- **Small features and bugs without a brief:** Default to **Simple** with a one-line justification (e.g. "Bug fix within existing UI surface; no new flows or IA changes"). Override to Complex only if the change touches multiple flows or introduces new information architecture.
- **UI-dominant items:** UX complexity is **N/A** — record "UI-only; no flow, IA, or behavioural changes". The design path recommendation from the rubric still applies.

This axis is **not** the same as behavioural change (below).

## Axis 2 — Behavioural change to users

Rate **Low / Medium / High** based on how much **users** must change habits, mental model, training, comms, or support load—not UI surface area alone.

| Level      | Meaning                                                                                                       |
| ---------- | ------------------------------------------------------------------------------------------------------------- |
| **Low**    | Fits existing expectations; no new habit; minimal comms.                                                      |
| **Medium** | New steps or labels users must learn; moderate comms or help.                                                 |
| **High**   | New workflow, role change, retraining, or high support risk; breaking change to how they think about the job. |

Small features and bugs: Default to **Low** with a one-line justification unless the change visibly alters user-facing behaviour (e.g. "Bug fix restores expected behaviour; no new habits required").

**Overlap with UX:** UX can be **Simple** and behavioural change **High** (a small UI change can redefine a core task). Document both separately.

## Axis 3 — Engineering complexity

**Before scoring:** Follow the **Integration points** steps in [`eng-complexity-rubric.md`](./eng-complexity-rubric.md): if the repo documents an integration catalog and recipe folder (for example `.claude/skills/README.md` plus `.claude/skills/integration-points/`, or your org’s equivalent), read the catalog and scan the recipes—do **not** assume a fixed list of pattern names from memory. If there is no catalog, the rubric tells you how to record **N/A**.

Then read the rest of the rubric and assign **Low / Medium / High** with 2–4 bullets tied to the spec, brief, or ticket. When intrinsic Eng is **Medium** or **High**, always state **which** integration recipes apply (if any), or explicitly **"No clear mapping — new pattern needed"** (and apply rubric escalation if required).

## Routing recommendation (default matrix)

Apply this **default** unless the user's org defines overrides in **how we work** docs. Always state **one primary** recommendation plus **when to escalate**.

**PM self-serve:** Valid for some orgs when the change is product-owned collateral only; if undefined, treat PM self-serve as "engineering workflow with no code change."

| Eng    | UX (brief) | Behavioural | Primary recommendation                                                                                    |
| ------ | ---------- | ----------- | --------------------------------------------------------------------------------------------------------- |
| Low    | Simple     | Low         | **Coding agent** — agent executes on the repo following documented standards; requester reviews the output. |
| Low    | N/A        | Low         | **Coding agent** only when the design path says the UI pattern is known and coding-agent-ready.           |
| Low    | Simple     | Med/High    | **Engineering workflow** — PM drives; align on comms/training and edge cases before build.               |
| Low    | N/A        | Med/High    | **Engineering workflow** — same as above.                                                                |
| Low    | Complex    | any         | **Engineering workflow** — design/IA validation; may still be PM-led with eng consult.                      |
| Medium | any        | Low/Med     | **Engineering workflow** — standard build path; PM pairs on spec/AC.                                     |
| Medium | any        | High        | **Engineering workflow** or **hand to eng** if rollout risk is high.                                     |
| High   | any        | any         | **Hand to eng** — eng owns execution and risk; PM owns intent and acceptance.                              |

**Coding agent** means the work is small and safe enough for an AI coding agent to implement directly, following repo standards the team documents (e.g. feature flags default OFF, structured logging not raw console, typed errors, lint, format, typecheck, validated inputs, service-layer patterns). If those standards are undefined, recommend **engineering workflow** until they exist. The requester reviews and merges.

**Design path (parallel recommendation):** The routing matrix determines **execution**. The **design path** from [`ux-design-path-rubric.md`](./ux-design-path-rubric.md) is **parallel** and tells the PM how to handle the design/UX dimension. Always present both. The design path never overrides execution—e.g. if Eng is High → **Hand to eng** stays primary even if design path says **Coding agent**. See reconciliation rules in the rubric.

**Escalation hints:** If assessment relied on `[INFERRED]` or `[UNKNOWN]` for critical areas, recommend **engineering workflow** at minimum until clarified.

## PR complexity (implementation increments)

This answers **how many PRs / increments** (and in what order), not **who executes** the work. It is **orthogonal** to the routing matrix: a **Coding agent** path can still ship as multiple increments; **Hand to eng** can be a single PR.

**When to include**

- **Always** when the user asks for PR count, an increment backlog, or “first increment” for a run.
- **Bet tier:** When an **approved** `Technical Spec.md`, integration plan, or equivalent exists, add a PR complexity subsection to Path A (or a standalone report in chat). If only a brief exists, set PR complexity to **Deferred** and list under open gaps—do not invent boundaries from product intent alone.
- **Small feature / bug fix:** Default **one increment** with a one-line rationale unless the scenario clearly requires multiple independently landable slices.

**How to produce it:** Read and follow [`pr-increment-rubric.md`](./pr-increment-rubric.md) (operating rules, flag-off acceptance criteria, integration-point discovery, report structure). Prefer the **fewest** increments that stay safe and reviewable; cap and re-scope guidance is in the rubric.

**Execution hint:** If delivery genuinely needs **more than ~3** landable increments or ordering is brittle, note in the assessment that coordination may favor **engineering workflow** even when the Eng axis is only Medium—this is **guidance**, not an automatic override of the matrix.

## Outputs

### Path A — Full assessment (Bet tier, or any item scoring above Coding agent)

#### 1. File: `bet-complexity-assessment.md` (same directory as the brief or spec you were given, or path the user chooses)

Use [`templates/pm/bet-complexity-assessment-template.md`](../../../templates/pm/bet-complexity-assessment-template.md) as the default shape if the org has no template. Minimum structure:

```markdown
# Complexity assessment — [feature / bet / bug name]

## Inputs used

- Brief: [path or "none"]
- Spec: [path or "none"]
- Scenario / description: [inline or "none"]

## Work-item tier

[Bet | Small feature | Bug fix]

## Axis scores

### UX complexity

- Classification: Simple | Complex | N/A (UI-only)
- Evidence: [bullets; cite Section 0, spec, or scenario]

### Design path

- Nature: [UX-dominant | UI-dominant | Mixed] — [one-line rationale]
- DS coverage: [Known pattern | Partial / unsure | Unknown / net new] — [one-line rationale; list any [INFERRED] items]
- UX complexity: [Simple | Complex | N/A] — [one-line rationale or "UI-only"]
- Design recommendation: [Coding agent | Designer review | Designer + Figma | Spec skill + front-end-designer skill]
- PM action: [what the PM should do next for the design dimension]

### Behavioural change

- Level: Low | Medium | High
- Evidence: [bullets]

### Engineering complexity

- Level: Low | Medium | High (final; note if intrinsic differed before integration-point escalation)
- Evidence: [bullets; tie to rubric]
- Integration mapping: [recipe file(s), "None — new pattern needed", or "N/A — no integration catalog in repo"]

### PR complexity (implementation increments)

Follow [`pr-increment-rubric.md`](./pr-increment-rubric.md). Minimum in this file:

- **Estimated PR count:** N
- **Recommendation:** Single increment | Multi-increment series
- **Why:** [1–3 sentences]
- **First increment for this run:** `<id>` — [title]
- **Detail:** [paste full increment blocks from rubric template] **or** link `pr-complexity-assessment.md`
- **Status:** [omit if sized] **Deferred** — [gaps] _(brief/spec-only; no implementation plan to slice)_

## Recommendation

- **Primary:** Coding agent | PM self-serve | Engineering workflow | Hand to eng
- **One-line why:** [synthesis]
- **If wrong, escalate when:** [triggers]

## Open gaps

- [UNKNOWN] / [INFERRED] items that could change the call
```

#### 2. Brief summary (only if a team brief file exists)

Append a short subsection under Section 0 (or immediately after it) in the brief:

```markdown
### Complexity routing summary

- **Recommendation:** [Coding agent | PM self-serve | Engineering workflow | Hand to eng]
- **Detail:** See `bet-complexity-assessment.md`.
```

If the user prefers not to edit the brief, skip this and mention it in chat.

#### 3. Spec-only path (no brief)

If only a spec exists: write **`bet-complexity-assessment.md`** as above when a durable artifact is needed. **`build-technical-spec`** requires **`## Complexity routing and delivery`** inside `Technical Spec.md` (see [`templates/pm/technical-spec-template.md`](../../../templates/pm/technical-spec-template.md)); when you are **not** running that workflow, add the same section (or a short block with recommendation + link to `bet-complexity-assessment.md`) **unless** the user declines to modify the spec file.

### Path B — Lightweight assessment (Coding agent recommendation)

When the assessment lands on **Coding agent**, a full file is not required. Instead, present a short block **in chat**:

```markdown
### Quick assessment — [name]

- **Tier:** [Small feature | Bug fix]
- **UX:** Simple — [one-line reason]
- **Design path:** [Nature] / [DS coverage] → [Design recommendation] — [one-line PM action]
- **Behavioural:** Low — [one-line reason]
- **Eng:** Low — [one-line reason]
- **PR complexity:** [Single increment | N increments — one line; or "Deferred — no spec"]
- **Recommendation:** Coding agent
- **Repo standards:** [tests, lint, typecheck, feature flags, logging, security—per org]
```

If the user requests a file or the item escalates during implementation, fall back to Path A.

## Guardrails

- Do **not** invent metrics, user research, or engineering facts.
- Mark unknowns `[UNKNOWN]`; inferred items `[INFERRED]` with reason.
- Keep the assessment **one to two pages**; depth lives in bullets, not prose.
- For bugs and small features, do **not** demand a full brief. A scenario or repro description is sufficient input.
- **PR complexity:** Do not invent PR boundaries from a product brief alone (no spec/plan). Do not fabricate integration-point names—discover them from the repo or list gaps per [`pr-increment-rubric.md`](./pr-increment-rubric.md).

## Quality check

- [ ] Work-item tier identified
- [ ] All three axes scored with evidence
- [ ] Design path classification completed (nature, DS coverage, UX complexity, design recommendation) per [`ux-design-path-rubric.md`](./ux-design-path-rubric.md)
- [ ] Recommendation matches the default matrix or documents an explicit override from **how we work**
- [ ] Design path recommendation is consistent with the execution recommendation (reconciliation rule applied)
- [ ] If Coding agent recommended, confirmed all three axes are at their lowest level (Eng Low, UX Simple or N/A with non-blocking design path, Behavioural Low)
- [ ] For Path A: `bet-complexity-assessment.md` written (or user declined file write—then paste full markdown in chat)
- [ ] If applicable: PR complexity addressed per [`pr-increment-rubric.md`](./pr-increment-rubric.md) (or explicitly **Deferred** with reason)
- [ ] Open gaps listed for PM/eng follow-up
