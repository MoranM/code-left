# Setup Code-Left

`setup-code-left` guides a team through installing the first local Code-Left skills bundle in a target repository.

It does not implement product features. It creates the agent-facing workflow that makes future implementation safer:

- one `integrate` orchestrator skill
- one `integration-points/` skill for a strong codebase-specific candidate
- product skills for bets, briefs, complexity, and specs
- a local README explaining the new flow

## When to use it

Use this skill when:

- a team wants to start adopting Code-Left
- engineering knowledge is still mostly implicit
- agents are already being used but implementation feels ad hoc
- a team wants an agent to map specs to documented playbooks before implementation

## What it produces

The usual output is a local skills folder in the target repo.

If the target repo has no agent-skill convention, use:

```text
skills/code-left/
  README.md
  integrate/
    SKILL.md
  integration-points/
    [first-integration-point]/
      SKILL.md
  product/
    build-product-brief/
      SKILL.md
    build-technical-spec/
      SKILL.md
    assess-work-item-complexity/
      SKILL.md
```

If the target agent expects another path, adapt the same structure to that path.

## The installed flow

After setup, users should be able to:

1. Create or provide a product spec or change package.
2. Invoke the local `integrate` skill.
3. Let the agent map the spec to available integration-point playbooks.
4. Get an implementation plan when playbooks exist.
5. Get a missing-playbook report when coverage is missing.
6. Execute the change in a feature branch only after confirmation.

## Related assets

- Natural-language setup spec: [../../NL-SPEC.md](../../NL-SPEC.md)
- Example outcome: [../../examples/first-pilot/](../../examples/first-pilot/)
- Integration candidate scout: [../map-integration-candidates/](../map-integration-candidates/)
- Integration orchestrator builder: [../build-integrate-skill/](../build-integrate-skill/)

## Missing playbook rule

The setup flow should make missing integration coverage visible. If a product spec cannot be mapped to an available integration-point playbook, the agent should stop and report the missing playbook instead of inventing an implementation path.
