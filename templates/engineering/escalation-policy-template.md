# Escalation policy

Use this optional template when review rules need to be explicit across playbooks.

## Autonomy levels

| Level | Meaning | Example |
| --- | --- | --- |
| Agent-safe | Agent may proceed with normal validation. | [example] |
| Product review | Product intent or user behavior needs confirmation. | [example] |
| Engineering review | Implementation risk needs engineer review. | [example] |
| Architecture escalation | System boundaries or platform capabilities may change. | [example] |
| Cannot proceed | Required context or validation is missing. | [example] |

## Agent-safe changes

Agents may proceed when:

- [condition]
- [condition]

## Requires product review

Stop for product review when:

- requested behavior is ambiguous
- acceptance criteria conflict
- copy, UX, analytics, or rollout expectations are unclear
- [local condition]

## Requires engineering review

Stop for engineering review when:

- permissions or data access rules are unclear
- a shared abstraction may change
- performance or reliability risk is introduced
- required validation cannot be run
- [local condition]

## Requires architecture escalation

Stop for architecture escalation when:

- new infrastructure is needed
- cross-service contracts change
- ownership boundaries are unclear
- the data model changes significantly
- [local condition]

## Cannot proceed

The agent cannot proceed when:

- required context is missing
- the requested change conflicts with documented policy
- safe integration point cannot be identified
- validation is blocked and no review path is defined

## Escalation report format

When stopping, the agent should report:

- requested change
- blocking issue
- affected files or systems
- options considered
- recommended next owner
- information needed to continue
