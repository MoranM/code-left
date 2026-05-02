# How we work

Living document: the **operating system** for turning context into shipped bets. Align PM, engineering, design, and agents on the same rails.

---

## Artifact chain

| Stage | Artifact | Owner | Required for |
| --- | --- | --- | --- |
| Direction | Where we want to get to | [role] | All non-trivial bets |
| Reality | Who we are now + learnings log | [role] | All non-trivial bets |
| Bet | Bet brief (`bet-brief.md` or your name) | PM / PM+EM | Feature bets |
| Routing | Bet complexity assessment | PM / EM | Before large eng work |
| Handoff | Technical spec | EM / engineer | Implementation |

Teams may rename files; keep **roles and gates** explicit.

---

## Bet tiers (define your own names)

| Tier | Typical input | Minimum artifacts |
| --- | --- | --- |
| **Small fix or tweak** | Repro or short scenario | Link to context if needed; may skip full bet brief per policy below |
| **Scoped enhancement** | Short spec or bullets | Bet brief lite or agreed template |
| **Larger bet** | Bet brief + assessment + spec | Full chain |

**Your policy for skipping a bet brief:** [e.g. copy-only and one surface → allowed]

---

## Complexity and routing

- **Who runs** [`assess-work-item-complexity`](../../skills/pm/assess-work-item-complexity/SKILL.md): [role]
- **Default matrix location:** [link or paste your routing rules]
- **When engineering must own execution:** [triggers]

---

## Unknowns and quality bar

- Unknown product facts: `[UNKNOWN]` until confirmed.
- Unknown engineering identifiers in specs: use placeholders defined in the technical spec skill (e.g. `[FLAG: slug]`).

---

## Review and launch

- **Design review:** [when required]
- **Security or privacy review:** [when required]
- **Analytics and event naming:** [owner and standard]
- **Rollout:** [feature flags, gradual rollout, kill switch]

---

## Escalation

| Situation | Escalate to | First action |
| --- | --- | --- |
| Strategy conflict between bet and vision doc | | |
| Evidence missing for high-risk bet | | |
| Implementation touches auth, money, or PII | | |

---

## Links

- [Issue tracker project]
- [Design system]
- [Engineering integration playbook or Code-Left orchestrator skill path in your repo]
