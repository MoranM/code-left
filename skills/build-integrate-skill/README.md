# Build Integrate Skill

`build-integrate-skill` helps an engineer create the orchestration layer for a Code-Left repository.

Code-Left is an operating model where engineers stop being the default implementors of every feature and instead design the system that safely turns product intent into production code. PM specs, prototypes, and POCs become inputs to a controlled integration pipeline. Coding agents execute that pipeline inside boundaries defined by engineering.

This skill does not implement product features. It builds the skill that will later orchestrate those implementations.

## Why This Exists

Coding agents are good at writing code, but production work usually fails at the integration layer:

- Where does this change belong?
- Which existing pattern must be reused?
- Which files are safe to touch?
- What validation, observability, permissions, rollout controls, and tests are required?
- When should the agent stop and ask for human review?

In many repositories, those answers live in senior engineers' heads. A Code-Left repository makes them explicit as integration contracts, instruction sets, templates, and validation gates.

`build-integrate-skill` creates the parent orchestration skill that ties those pieces together.

## The Orchestration Concept

An integration orchestrator is the agent-facing workflow that turns a product change package into a safe production change.

It is responsible for:

1. Accepting product intent, such as a spec, prototype, POC, ticket, screenshot, or pasted description.
2. Extracting the essence of the requested change in product terms.
3. Classifying the change into one or more known integration point types.
4. Loading the relevant playbooks for those integration points.
5. Producing a dependency-ordered implementation plan.
6. Asking for confirmation before code changes begin.
7. Executing only through allowed seams and approved abstractions.
8. Running the repository's required validation and review policy.
9. Reporting what changed, how to test it, and what still needs review.

The orchestrator is the bridge between PM-owned intent, agent-owned execution, and engineer-owned safe integration.

## When To Use This Skill

Use `build-integrate-skill` when starting Code-Left adoption in a new repository or when formalizing an existing agent workflow.

It is especially useful when:

- A repo has repeated feature work that follows recognizable patterns.
- Engineers want agents to implement through known seams instead of doing repo archaeology every time.
- Product artifacts are becoming structured enough to drive implementation.
- The team wants a clear division of responsibility between PM intent, agent execution, and engineering guardrails.
- You already have, or plan to create, smaller integration-point playbooks such as "new page", "new endpoint", "new event handler", or "new background worker".

## What This Skill Produces

The output is usually a new skill directory for the target repository:

```text
.claude/skills/integrate/SKILL.md
.claude/skills/integrate/README.md
```

The generated `SKILL.md` is the operational workflow an agent follows when integrating a real feature.

The generated README explains the orchestrator's purpose, expected inputs, phase model, integration-point structure, validation requirements, and maintenance rules.

## What The Target Repo Needs

A repository does not need to be fully Code-Left ready before using this skill, but the builder needs enough context to design the first safe workflow.

Useful inputs include:

- Product artifact examples: specs, POCs, tickets, prototypes, or change packages.
- Common change categories: page, API endpoint, event handler, worker, notification flow, admin tool, workflow step, or another local pattern.
- Known extension points: where new things are registered, mounted, scheduled, routed, rendered, or invoked.
- Engineering rules: architecture boundaries, data access patterns, auth, permissions, logging, metrics, feature flags, migrations, and dependency rules.
- Validation policy: typecheck, build, tests, lint, formatting, migration checks, security checks, accessibility checks, or manual review gates.
- Escalation policy: changes that require engineer review, product review, architecture review, or cannot be handled autonomously.

If these inputs are missing, the skill helps discover them from the repository and asks focused questions only where needed.

## Integration Points

Integration points are the known seams through which agents are allowed to modify the system.

Examples:

- New page
- New API endpoint
- New event handler
- New background worker
- New notification flow
- New workflow step
- New admin tool
- Extension of an existing domain flow

Each integration point should eventually have its own playbook that defines:

- Purpose and allowed scope
- Required file locations and registration paths
- Required contracts, inputs, outputs, and lifecycle expectations
- Required safeguards such as retries, idempotency, permissions, rollout controls, logging, and metrics
- Reuse expectations and canonical examples
- Escalation triggers
- Validation checklist

The orchestrator does not replace these playbooks. It discovers them, selects the relevant ones, sequences them, and enforces the stop points around them.

Use the [map-integration-candidates](https://github.com/MoranM/code-left/blob/main/skills/map-integration-candidates/README.md) skill to locate a potential candidates for integration points in your codebase.

## Generated Orchestrator Phases

A strong integration orchestrator usually follows this phase model:

1. **Prepare the workspace:** Confirm branch, working tree, ownership, and whether implementation is allowed.
2. **Load the foundation:** Read repository rules, architecture docs, design system guidance, and safety constraints.
3. **Collect the source:** Ask where the product intent lives.
4. **Explore the source:** Summarize user outcome, flows, data, side effects, UI surfaces, and operational implications.
5. **Map to integration points:** Dynamically discover playbooks and explain which apply or do not apply.
6. **Plan execution:** Load selected playbooks and produce a dependency-ordered plan.
7. **Execute through seams:** Modify only approved areas and stop on missing primitives or unclear policy.
8. **Run quality gates:** Execute the repo's required validation and review checks.
9. **Report completion:** Summarize changes, testing steps, rollout state, review path, and known gaps.

## What Good Looks Like

A good generated orchestrator makes agent behavior predictable. It should:

- Separate product understanding from implementation planning.
- Use dynamic discovery instead of hardcoded integration-point lists.
- Require user confirmation before code changes.
- Treat engineering rules as mandatory, not suggestions.
- Define explicit stop conditions for ambiguity and architectural risk.
- Route high-risk changes to review instead of forcing autonomous implementation.
- Improve over time when agents struggle or reviewers find recurring mistakes.

## Readiness Checklist

Before using the generated orchestrator for real production work, confirm:

- The repo has at least one clear integration point or a narrow first change class.
- The orchestrator knows where to find integration-point playbooks.
- The workflow distinguishes safe local decisions from escalation triggers.
- Validation commands are exact and runnable in the target repo.
- The completion report includes changed files, test steps, rollout notes, known gaps, and review path.
- The team has a habit of updating playbooks when the agent exposes missing rules.

The goal is not a perfect universal workflow on day one. Start narrow, run real changes through the system, and strengthen the playbooks whenever ambiguity repeats.
