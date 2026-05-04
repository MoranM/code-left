# Setup Code-Left

`setup-code-left` guides a team through the first Code-Left setup for a target repository or product area.

It does not implement product features. It helps create the operating artifacts needed for a first safe pilot:

- one repo readiness assessment
- one selected pilot change type
- one integration-point playbook
- one real product spec or change package wrapper for agent handoff
- one recommended agent execution path
- one feedback loop for review learnings

## When to use it

Use this skill when:

- a team wants to start adopting Code-Left
- engineering knowledge is still mostly implicit
- agents are already being used but implementation feels ad hoc
- a team needs help connecting templates, playbooks, and skills into one first pilot

## What it produces

The usual output is a first pilot package in the target repo or handbook:

```text
code-left/
  repo-readiness-assessment.md
  integration-point-playbook.md
  change-package.md
  first-pilot-plan.md
  review-learnings.md
```

The exact path can vary. The important part is that the package is easy for product, engineering, and agents to find.

## Related assets

- Example outcome: [../../examples/first-pilot/](../../examples/first-pilot/)
- Starter guide: [../../docs/getting-started.md](../../docs/getting-started.md)
- Engineering templates: [../../templates/engineering/](../../templates/engineering/)
- Integration candidate scout: [../map-integration-candidates/](../map-integration-candidates/)
- Integration orchestrator builder: [../build-integrate-skill/](../build-integrate-skill/)

## How this differs from `build-integrate-skill`

`setup-code-left` helps a team create the first Code-Left pilot package.

`build-integrate-skill` creates a reusable integration orchestrator skill after the team knows which playbooks and validation rules should drive implementation.

In most teams, use `setup-code-left` first.

## Missing playbook rule

The setup flow should make missing integration coverage visible. If a product spec cannot be mapped to an available integration-point playbook, the agent should stop and report the missing playbook instead of inventing an implementation path.
