# Contributing to Code-Left

Code-Left is a practical library for making product intent, engineering integration knowledge, and agent execution work together safely.

Contributions should make the repo clearer, more usable, or more operationally useful for teams adopting agent-assisted delivery.

## Good contributions

Useful contributions include:

- clearer docs and examples
- new or improved templates
- integration-point playbook patterns
- agent-neutral workflow improvements
- issue reports about confusing setup steps
- fixes for broken links, typos, or unclear terminology

## Keep it agent-neutral

Use generic terms such as:

- coding agent
- agent skill
- agent instruction set
- agent config path
- `<agent-config>/skills/...`

Avoid tying core docs to a specific agent tool. Tool-specific adapters can be added later in dedicated docs.

## Writing style

Keep docs:

- practical before philosophical
- concise enough to use during real work
- explicit about ownership, validation, and escalation
- focused on repeatable change types
- clear about what is required now versus optional later

## Suggesting a playbook

When suggesting an integration-point playbook, include:

- the change type
- where it usually enters the system
- existing examples
- required safeguards
- validation requirements
- escalation triggers

Use the "Suggest integration playbook" issue template when opening an issue.

## Pull requests

Before opening a pull request:

- check that links resolve
- keep examples agent-neutral
- update `CHANGELOG.md` under `Unreleased`
- explain whether the change affects first-time setup, advanced usage, or both
