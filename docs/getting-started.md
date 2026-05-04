# Getting started with Code-Left

Use this guide when you want the smallest practical setup. Do not try to make the whole repo AI-ready at once. Pick one repeated, low-risk change type and learn from a real implementation.

## The first pilot

The first pilot has three artifacts:

1. A repo readiness assessment.
2. One integration-point playbook.
3. One real product spec, or a change package that wraps the product spec for agent handoff.

Those three files are enough to test whether product intent can move toward production through an engineering-defined seam.

For a filled-in version of this flow, see [../examples/first-pilot/](../examples/first-pilot/). The example also includes two useful support files: an agent implementation plan and review learnings.

If you want an agent to guide the setup, use [../skills/setup-code-left/](../skills/setup-code-left/). That skill produces the three starter artifacts plus a first-pilot plan and a review-learnings placeholder.

## Step 1 - Assess the repo

Use [../templates/engineering/repo-readiness-assessment.md](../templates/engineering/repo-readiness-assessment.md).

Look for a change type that is:

- repeated across the product
- low risk if implemented incorrectly
- already handled consistently by engineers
- easy to validate with existing checks
- valuable enough to repeat after the pilot

Good first candidates are usually internal pages, admin tools, bounded UI additions, simple notification variants, small workflow extensions, or event handlers attached to an existing event contract.

Avoid starting with migrations, new infrastructure, permissions redesign, shared abstractions, cross-service contracts, or high-risk customer-facing flows.

## Step 2 - Document one integration point

Use [../templates/engineering/integration-point-playbook-template.md](../templates/engineering/integration-point-playbook-template.md).

The playbook should answer the questions an engineer normally answers from memory:

- Where does this change type belong?
- Which files or modules may be touched?
- Which existing patterns must be reused?
- What safeguards are mandatory?
- What validations must pass?
- When must the agent stop and ask for review?

Keep the first playbook short. It only needs to be good enough for one real pilot.

## Step 3 - Provide one real spec or change package

Use [../templates/engineering/change-package-template.md](../templates/engineering/change-package-template.md).

The change package is the thin agent-facing wrapper around product intent. It should either link to the product spec or embed the product spec directly. Do not create a second source of truth.

Use the template when the existing spec does not clearly expose the goal, requested behavior, acceptance criteria, non-goals, edge cases, references, suspected integration point, and rollout notes.

## Step 4 - Run one agent-assisted change

Give the agent:

- the change package
- the integration-point playbook
- any relevant existing examples
- the validation commands

Ask the agent to classify the change, explain why the playbook applies, produce a short implementation plan, and stop before editing if the playbook is missing required information.

If the spec cannot be mapped to an available integration-point playbook, the agent should stop and report the missing playbook. It should not invent a new implementation path outside documented repo seams.

Agent skill files in this repo are portable markdown instruction sets. Source copies live under [../skills/](../skills/). If your agent tool expects a different location, copy or adapt them into its configured path, such as `<agent-config>/skills/...`.

## Step 5 - Strengthen the playbook

After the pilot, update the playbook based on what actually happened.

Capture:

- decisions the agent guessed
- rules reviewers had to explain
- files the agent touched incorrectly
- validations that were missing or too vague
- escalation triggers that were discovered late

The goal is not a perfect document. The goal is to stop rediscovering the same integration knowledge for every change.

## When to add more structure

Use the optional engineering templates only when the first pilot exposes repeated needs:

- Use [../templates/engineering/agent-instruction-template.md](../templates/engineering/agent-instruction-template.md) when the workflow should become a reusable agent skill.
- Use [../templates/engineering/validation-policy-template.md](../templates/engineering/validation-policy-template.md) when checks differ by change type.
- Use [../templates/engineering/escalation-policy-template.md](../templates/engineering/escalation-policy-template.md) when review rules need to be explicit.

Expand only after one playbook works.
