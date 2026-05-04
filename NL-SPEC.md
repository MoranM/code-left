# Code-Left bootstrap spec

Use this when Code-Left is not installed in your repository yet.

This file is a bootstrap instruction for a coding agent. It points the agent to this GitHub repo as source material and tells it to follow the `setup-code-left` skill to install a local Code-Left skills bundle.

## Copy-paste prompt

```text
I want to set up Code-Left in this repository.

Use this source repo as the reference:
https://github.com/MoranM/code-left

Follow the setup workflow in:
https://github.com/MoranM/code-left/blob/main/skills/setup-code-left/SKILL.md

Do not clone the Code-Left repo into this codebase.
Create a local Code-Left skills folder for this repo.
Start by inspecting this repo and finding one strong integration-point candidate based on existing codebase conventions.
Do not implement a product feature during setup.
```

## Source repo

Use `https://github.com/MoranM/code-left` as the source of truth.

The main workflow is:

- `skills/setup-code-left/SKILL.md`

Supporting references:

- `skills/build-integrate-skill/SKILL.md`
- `skills/map-integration-candidates/SKILL.md`
- `skills/pm/build-product-brief/SKILL.md`
- `skills/pm/build-technical-spec/SKILL.md`
- `skills/pm/assess-work-item-complexity/SKILL.md`
- `examples/first-pilot/`

## Required outcome

The target repo should get a local skills folder.

Default shape when the repo has no stronger convention:

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

If the target repo already has an agent-skill convention, adapt this structure to that convention.

## Hard rules

- Do not clone this repo into the target repo.
- Do not copy the whole repo.
- Do not copy every template.
- Do not implement a product feature during setup.
- Do not invent integration playbooks for weak or unclear repo areas.
- Do not create an `integrate` skill that can bypass playbooks.
- If no strong integration-point candidate exists, stop with a setup-blocked report.

## Installed flow

After setup, the target repo should support this flow:

1. User provides a product spec or change package.
2. User invokes the local `integrate` skill.
3. The agent maps the spec against local integration-point skills.
4. If required playbooks exist, the agent creates an implementation plan.
5. If required playbooks are missing, the agent reports the missing playbook.
6. After confirmation, the agent implements the change in a feature branch through selected playbooks.

The correct end state is not "the repo is fully Code-Left ready."

The correct end state is "the repo has a local Code-Left skills bundle with an integrate orchestrator and at least one real integration-point playbook, or a clear setup-blocked report."
