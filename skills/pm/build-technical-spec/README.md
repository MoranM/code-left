# build-technical-spec

Turns a **bet brief** (or org equivalent) into a **standalone technical specification**: user stories, functional requirements, edge cases, success criteria, an explicit product contract, and **`## Complexity routing and delivery`** (execution routing, design path, engineering complexity, PR increments) so coding and implementation agents know **how** to handle the work—not only **what** to build.

**Team templates:** Use your org’s technical spec outline when you have one; [`technical-spec-template.md`](../../../templates/pm/technical-spec-template.md) is the Code-Left **reference / gap-check** shape. If the org template omits the complexity section, **add it** from the reference template.

The resulting spec can be loaded into an implementation agent directly, or wrapped in an engineering change package when the handoff needs a shorter agent-facing artifact. The agent should map the spec or package against available integration-point playbooks before implementation.

## When to use

- After a bet brief exists (preferred) or with explicit intent for spec-only mode.
- When the brief changed or stakeholders added comments—update the spec in place.

## Files

- [SKILL.md](./SKILL.md)
- Reference template: [`templates/pm/technical-spec-template.md`](../../../templates/pm/technical-spec-template.md)

## Companion

[`assess-work-item-complexity`](../assess-work-item-complexity/SKILL.md) (including [`pr-increment-rubric.md`](../assess-work-item-complexity/pr-increment-rubric.md)) is **mandatory step 0** of `build-technical-spec`; results are **embedded in the spec**, not only in chat.
