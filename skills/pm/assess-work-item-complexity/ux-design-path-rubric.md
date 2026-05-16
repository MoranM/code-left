# UX / UI design-path rubric

Use this file to classify the **design path** for a work item and recommend the right PM / design action.
Edit definitions here as the team's bar evolves; [`SKILL.md`](./SKILL.md) references this document.

## Step 1 — Nature of change

Classify the work item as one of:

| Classification  | Definition                                                                                                      | Examples                                                                                      |
| --------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **UX-dominant** | Changes _how users think, navigate, or make decisions_. Involves flows, information architecture, or behaviour. | New user journey, restructured navigation, new decision point, onboarding flow, role change.  |
| **UI-dominant** | Changes _what users see_ within an existing flow. Layout, styling, component usage, copy, visual polish.        | Restyling a card, swapping an icon, adjusting spacing, adding a banner to an existing page.   |
| **Mixed**       | Both UX and UI are materially affected. Neither is trivial relative to the other.                               | New tab with new flow _and_ new visual patterns; redesigned page that changes IA and visuals. |

Pick one and provide a one-line rationale.

## Step 2 — Design system gate

Determine whether the visual / component work is **supported by the existing design system** (DS) or established product patterns.

| DS coverage           | Definition                                                                                                                                                 |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Known pattern**     | Every component, token, and layout convention needed already exists (design-system primitives, styling tokens, established page patterns in the codebase). |
| **Partial / unsure**  | Most of it maps to DS, but one or two elements are new or the agent cannot confirm coverage. Mark `[INFERRED]` and state what is uncertain.                |
| **Unknown / net new** | The work requires visual patterns, components, or layouts that do not exist in the DS today. A designer should explore and extend the DS.                  |

### Checklist (answer each; if any answer is No or Unsure, coverage is at most Partial)

- [ ] All required UI components map to existing design-system or product primitives.
- [ ] Colour, spacing, and typography use existing tokens or conventions (no ad-hoc one-offs unless already standard).
- [ ] Page layout follows an established pattern already present in the app (e.g. existing tab structure, card grid, modal/drawer pattern).
- [ ] No net-new icon set, illustration style, or animation pattern is required.

If you **cannot verify** a checklist item from the repo or available docs, mark it `[INFERRED]` and default to **Partial / unsure**.

## Step 3 — UX complexity (Section 0 model)

**Applies to:** `UX-dominant` and `Mixed` items.
**Skip for:** `UI-dominant` items — record "N/A — UI-only; no flow, IA, or behavioural changes" and move to the decision table.

Use the three criteria from [`bet-brief-template.md`](../../../templates/pm/bet-brief-template.md) Section 0:

| Criterion                    | Simple                               | Complex                                          |
| ---------------------------- | ------------------------------------ | ------------------------------------------------ |
| **Scenarios**                | 1-2 clear, linear scenarios          | 3+ scenarios with branching user paths           |
| **Flow impact**              | Small correction to an existing flow | New flow or major restructure of an existing one |
| **Information architecture** | Same IA with minor additions         | Challenges or restructures existing IA           |

**Decision rule:** All three Simple → **Simple**. Any one Complex → **Complex**.

If the brief has Section 0 filled, copy it. If not, infer with `[INFERRED]` and list unknowns.

## Decision table — PM / design recommendation

Combine the outputs of Steps 1–3 to determine the recommended design path:

| Nature (Step 1) | DS coverage (Step 2) | UX complexity (Step 3) | Design path recommendation                                                                                                                                            |
| --------------- | -------------------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **UI-dominant** | Known pattern        | N/A                    | **Coding agent** — agents can implement using DS. No designer needed (subject to Eng + Behavioural axes in routing matrix).                                           |
| **UI-dominant** | Partial / unsure     | N/A                    | **Designer review** — designer confirms or extends DS for uncertain elements; then agents implement. Flag DS gaps to improve the system.                              |
| **UI-dominant** | Unknown / net new    | N/A                    | **Designer** — designer explores and creates the new pattern; feed learning back into the DS.                                                                         |
| **UX-dominant** | Known pattern        | Simple                 | **Spec skill + front-end-designer skill** — spec workflow generates implementation-ready framing; front-end-designer skill produces the UI. No Figma needed. |
| **UX-dominant** | Partial or Unknown   | Simple                 | **Designer review** — designer validates uncertain DS elements and simple UX; then spec skill can proceed.                                                            |
| **UX-dominant** | any                  | Complex                | **Designer + Figma** — traditional design process. Designer owns exploration in Figma; spec work pauses on UX sections until design is ready.                         |
| **Mixed**       | Known pattern        | Simple                 | **Spec skill + front-end-designer skill** — treat like UX-dominant Simple with known DS.                                                                              |
| **Mixed**       | Partial or Unknown   | Simple                 | **Designer review** — designer validates DS gaps; then spec skill proceeds.                                                                                           |
| **Mixed**       | any                  | Complex                | **Designer + Figma** — traditional design process.                                                                                                                    |

### Reconciliation with Eng / Behavioural axes

The design path recommendation is a **parallel** recommendation. It does **not** override the primary execution recommendation from the routing matrix (Coding agent / Engineering workflow / Hand to eng).

- If the routing matrix says **Engineering workflow** or **Hand to eng**, that remains the primary execution path. The design path tells the PM _how to handle the design/UX dimension_ alongside that execution path.
- If the routing matrix says **Coding agent** but the design path says **Designer + Figma**, the PM should involve a designer for the UX/visual work _before_ handing to the coding agent for implementation.
- Always present both recommendations together so the PM sees the full picture.

### "Spec skill + front-end-designer skill" explained

When the design path recommends this, the PM should:

1. Run their technical-spec workflow (e.g. `build-technical-spec`) to produce implementation-ready framing (user stories, acceptance criteria, component mapping).
2. Use a front-end-designer skill or equivalent to generate production-grade UI within the existing DS.
3. The combination replaces the need for a separate Figma design phase for simple, DS-covered changes.

## Output format

Include in your assessment (Path A or Path B):

```markdown
### Design path

- **Nature:** [UX-dominant | UI-dominant | Mixed] — [one-line rationale]
- **DS coverage:** [Known pattern | Partial / unsure | Unknown / net new] — [one-line rationale; list any [INFERRED] items]
- **UX complexity:** [Simple | Complex | N/A] — [one-line rationale or "UI-only"]
- **Design recommendation:** [Coding agent | Designer review | Designer + Figma | Spec skill + front-end-designer skill]
- **PM action:** [what the PM should do next for the design dimension]
```
