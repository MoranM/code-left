# Code-Left implementation guide

This guide explains how to move from one pilot to a repeatable Code-Left operating model.

Code-Left works when product intent, engineering integration rules, and agent execution are connected by explicit artifacts.

## 1. Choose integration points

An integration point is a known seam where a common change type enters the system.

Examples:

- new page
- API endpoint
- event handler
- background worker
- notification variant
- workflow step
- admin tool
- bounded extension of an existing domain flow

Strong integration points have focused responsibility, consistent examples, clear ownership, and obvious validation. Weak integration points have scattered logic, unclear boundaries, or many hidden dependencies.

Use [../skills/map-integration-candidates/](../skills/map-integration-candidates/) when you need help finding candidates in a target repo.

## 2. Write one playbook per safe seam

Each playbook should define:

- purpose and allowed scope
- when to use it and when not to use it
- required file locations and registration paths
- contracts, inputs, outputs, and lifecycle rules
- required safeguards
- reuse expectations and canonical examples
- validation checklist
- escalation triggers

Use [../templates/engineering/integration-point-playbook-template.md](../templates/engineering/integration-point-playbook-template.md) as the starting point.

The playbook should be specific enough that an agent can identify the right implementation path without doing repo archaeology from scratch.

## 3. Package product intent

Product intent should arrive as a change package, product brief, technical spec, prototype, or ticket with enough structure to drive implementation.

At minimum, include:

- goal
- requested behavior
- acceptance criteria
- non-goals
- edge cases
- references
- suspected integration point
- data, permissions, and rollout notes when relevant

Use [../templates/engineering/change-package-template.md](../templates/engineering/change-package-template.md) for engineering-facing requests, and [../templates/pm/](../templates/pm/) when the work needs product bet context or a full technical spec.

## 4. Define validation as part of the workflow

Validation is part of the integration model, not cleanup after implementation.

Start with exact commands the repo already supports:

- typecheck
- unit or integration tests
- lint
- build
- migration checks
- accessibility checks
- security or policy checks

Add [../templates/engineering/validation-policy-template.md](../templates/engineering/validation-policy-template.md) when different change types need different gates.

## 5. Define escalation triggers

Agents should not push through architectural ambiguity. A good playbook tells them when to stop.

Common escalation triggers:

- new permissions model
- new infrastructure primitive
- cross-service contract change
- shared abstraction change
- data ownership ambiguity
- missing validation path
- unclear user-facing behavior
- rollout or operational risk

Add [../templates/engineering/escalation-policy-template.md](../templates/engineering/escalation-policy-template.md) when these rules need to be shared across playbooks.

## 6. Turn repeated workflows into agent instructions

After one or two real pilots, repeated steps can become an agent instruction set.

Use [../templates/engineering/agent-instruction-template.md](../templates/engineering/agent-instruction-template.md) to define:

- accepted inputs
- required first reads
- classification rules
- execution boundaries
- stop conditions
- quality gate
- completion report

Agent instruction sets in this repo are portable markdown files. Source copies live under [../skills/](../skills/). Teams can copy or adapt them into the configured path used by their agent tool, such as `<agent-config>/skills/...`.

Use [../skills/build-integrate-skill/](../skills/build-integrate-skill/) when you are ready to create a repo-specific integration orchestrator.

## 7. Improve the system from real failures

The Code-Left loop is:

1. Run a real change through a playbook.
2. Watch where the agent guesses, stalls, or violates a pattern.
3. Convert that failure into a clearer rule, example, check, or escalation trigger.
4. Repeat on the same change type until it becomes predictable.
5. Expand to the next change type.

Do not try to automate all delivery at once. Code-Left adoption compounds through narrow, repeated seams.
