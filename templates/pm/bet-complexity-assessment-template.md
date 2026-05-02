# Bet complexity assessment — [bet or work item name]

Use this after a bet brief exists, or with a scenario-only description for small fixes.  
Routing should reflect **product and behavior risk**, not only code size.

---

## Inputs used

- **Where we want to get to:** [path or none]
- **Who we are now:** [path or none]
- **How we work:** [path or none]
- **Bet brief:** [path or none]
- **Technical spec:** [path or none]
- **Scenario or notes:** [inline or none]

---

## Work item tier

[ Bet | Scoped enhancement | Small fix ]

---

## Axis scores

### UX complexity

- **Classification:** Simple | Complex
- **Evidence:** [cite Section 0 of the bet brief, or scenarios, or mark `[INFERRED]` with reason]

### Behavioral change to users

- **Level:** Low | Medium | High
- **Evidence:** [habits, training, comms, support load, trust, positioning—not only UI surface area]

### Engineering complexity

- **Level:** Low | Medium | High
- **Evidence:** [tie to your engineering rubric; migrations, auth, new integrations, blast radius]
- **Integration mapping (optional):** [If your repo has integration-point playbooks, cite them. Otherwise: “No catalog in repo” or “N/A — intrinsic Low”.]

---

## Recommendation

- **Primary:** Coding agent | PM self-serve | Engineering workflow | Hand to engineering
- **One-line why:** [synthesis including product context, not only LOC]
- **If wrong, escalate when:** [triggers]

---

## Open gaps

- `[UNKNOWN]` / `[INFERRED]` items that could change the call
