# assess-work-item-complexity

Produces an **evidence-based routing recommendation** for a bet, small feature, or bug fix across UX complexity, user behavioural change, engineering complexity, and design path. When an approved spec exists or the user asks for delivery slices, it also covers **PR complexity** (increment count and backlog) using the same rules as wisdomcom **assess-pr-complexity**. Works with **your org’s** brief, spec, ticket, or notes; Code-Left templates are optional **reference** shapes (see [SKILL.md](./SKILL.md)).

Aligned with wisdomcom-monorepo **assessBetComplexity** + **assess-pr-complexity**; paths and skill names match the Code-Left repo.

## When to use

- Before deep technical-spec work (including quick-fix escalation decisions).
- When triaging whether a coding agent can implement directly or engineering should own execution.

## Files

- [SKILL.md](./SKILL.md)
- [eng-complexity-rubric.md](./eng-complexity-rubric.md)
- [ux-design-path-rubric.md](./ux-design-path-rubric.md)
- [pr-increment-rubric.md](./pr-increment-rubric.md)

## Output artifact

`bet-complexity-assessment.md` next to the brief or spec when the work is a bet, large, high-risk, repeated, disputed, user-requested as a durable artifact, or routes above **Coding agent**. For low-risk coding-agent work, the skill can return a quick chat assessment instead.
