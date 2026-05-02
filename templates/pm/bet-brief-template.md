# [Bet name] — Bet brief

Every product addition is a **bet** on improving value for customers or users. This brief captures intent, outcomes, and scope before implementation.

**Context used (required)** — Link or path to each layer your team maintains:

- **Where we want to get to:** [path or link]
- **Who we are now:** [path or link]
- **How we work:** [path or link]
- **Context source inventory (optional):** [path or link]

Implementation detail belongs in `Technical Spec.md`, not here.

---

## 0. UX complexity

**Classification:** Simple / Complex

Assess the following three criteria and provide a one-line rationale for each:

| Criterion | Simple | Complex |
| --- | --- | --- |
| **Scenarios** | 1–2 clear, linear scenarios | 3+ scenarios with branching paths |
| **Flow impact** | Small correction to an existing flow | New flow or major restructure |
| **Information architecture** | Same IA with minor additions | Challenges or restructures existing IA |

**Decision rule:** If all three are Simple, classify **Simple**. If any is Complex, classify **Complex**.

- **Scenarios:** [Simple/Complex] — [rationale]
- **Flow impact:** [Simple/Complex] — [rationale]
- **Information architecture:** [Simple/Complex] — [rationale]

---

### Complexity routing summary _(optional — fill after assessment)_

- **Recommendation:** [Coding agent | PM self-serve | Engineering workflow | Hand to engineering]
- **Detail:** See `bet-complexity-assessment.md` (if produced).

---

## 1. Intentions statement

Complete this sentence:

This bet will help **[primary user or segment]** to **[job or outcome]** and overcome **[problem today]** so that they feel **[emotion or confidence shift]**.

---

## 2. The promise

After this ships, users feel:

- [ ]
- [ ]
- [ ]

What meaningful change do they experience in daily work?

---

## 3. Core outcome (not features)

**One sentence transformation:** Before → After

**Before:** [State today]  
**After:** [State after the bet lands]

---

## 4. Target user and context

- **Primary:** [segment or persona]
- **Not for (now):** [explicit]
- **Moment of need:** [when this matters]
- **Trigger:** [what causes the need]

---

## 5. Affected user journeys

Each line must use four parts separated by ` / ` (space-slash-space). Use `[UNKNOWN]` for any missing slot.

`[the user] / [the intent] / [the action] / [the outcome]`

Examples:

- `Billing admin / reduce failed renewals / review failed payments dashboard / fewer involuntary churns next month`
- `End user / finish a task faster / use the new shortcut / completes core action in under two minutes`

List:

1. [user] / [intent] / [action] / [outcome]
2. [user] / [intent] / [action] / [outcome]

---

## 6. Key user scenarios

### Scenario 1 — [title]

1. [Step]
2. [Step]

### Scenario 2 — [title]

1. [Step]

---

## 7. Placement and rollout

- **Phase 1:** [where it lives first]
- **Phase 2:** [expansion if any]

---

## 8. Success signals

Define 3–5 measurable or observable signals.

- [Signal 1]
- [Signal 2]

---

## 9. Out of scope

- [Non-goal 1]
- [Non-goal 2]

---

## 10. Product inspiration

- **Borrow:** [product or pattern] — [why]
- **Avoid:** [anti-pattern] — [why]

---

## 11. Decisions and constraints

- [Decision or constraint]
- [Open question]

---

## 12. Risks and open questions

- **Risk:** [what could fail] — **Mitigation idea:** [how to de-risk]
- **Open question:** [what we still need to learn]

---

## Spec split tracking _(optional — fill when specs are split)_

When a large bet is split into multiple technical specs, list them here for traceability.

1. **Title:** [name] — **Scope:** [1–2 sentences] — **Dependencies:** [none or list] — **Primary surfaces:** [URLs or triggers] — **Target spec path:** [file path]
