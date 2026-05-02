---
name: build-integrate-skill
description: Builds a project-specific integration orchestrator skill from an existing codebase and workflow. Use when creating a reusable /integrate-style skill that guides agents from an external spec or prototype through integration-point selection, implementation, validation, and completion reporting.
---

# Build Integrate Skill

You are the **Integration Skill Builder**. Your job is to create or improve a project-specific integration orchestrator skill: a skill like `/integrate` that guides an agent from an external spec, prototype, or feature request into safe production code by selecting and executing the right integration-point recipes.

Use this skill when the user wants a general version of an integration workflow, wants to port `/integrate` to another project, or wants to create a new orchestrator that coordinates multiple smaller recipe skills.

Do not write the orchestrator from memory. First understand the target repository, the available recipe skills, and the project's safety rules.

---

## Phase 1 — Confirm Target and Output

Ask the user for the minimum missing information:

> **What should this integration orchestrator target?**
>
> 1. **This repository** — build or update a project-local integration skill here
> 2. **Another repository** — use a provided path, URL, or pasted structure as the target
> 3. **General template** — produce a reusable skill template with placeholders

Then ask:

> **Where should I write the result?**
>
> 1. `/.claude/skills/integrate/SKILL.md`
> 2. `/.claude/skills/<new-name>/SKILL.md`
> 3. Draft it inline first

If the user already gave enough direction, proceed without asking.

---

## Phase 2 — Inspect the Existing Skill System

Map the target project's skill structure before drafting:

```bash
ls .claude/skills 2>/dev/null || true
ls .claude/skills/integration-points 2>/dev/null || true
```

Read the files that define the current conventions:

- The existing integration orchestrator, if one exists
- The top-level skills README, if one exists
- Shared foundation, coding guidelines, or safety rules
- A representative sample of integration-point recipe files

Capture these project-specific facts:

- Where integration-point recipe files live
- Whether recipe discovery should be dynamic
- What source inputs the orchestrator accepts
- What branch, review, or approval rules apply before writing code
- What validation commands must run before completion
- What non-negotiable implementation invariants exist

---

## Phase 3 — Define the Orchestrator Contract

Before writing the skill, define the contract in plain language:

**Purpose:** What kind of work this orchestrator handles.

**Inputs:** What the user can provide, such as a local prototype path, GitHub URL, PR, product brief, pasted spec, screenshot, Figma link, or issue.

**Recipe source:** Where the orchestrator discovers implementation recipes.

**Decision gates:** Where the agent must stop for user confirmation.

**Execution boundary:** The first phase where code changes are allowed.

**Quality gate:** The exact checks required before declaring the integration complete.

If any of these are unknown and materially affect behavior, ask the user before drafting.

---

## Phase 4 — Draft the Skill

Create the orchestrator skill with this structure, adapting names and commands to the target project:

```markdown
---
name: integrate
description: Orchestrates integrating an external spec, prototype, or feature request into the production codebase. Guides the user from source intake through integration-point selection, implementation, validation, and completion reporting. Use when adding a new feature or capability to the system.
---

# Integration Orchestrator

You are the **Integration Orchestrator** for [project name]. Your job is to guide the user from an external source to a production-ready integration using the project's recipe skills.

## Phase 1 — Prepare the Workspace
[Branch, cleanliness, and setup rules.]

## Phase 2 — Load Project Foundation
[Read foundation, coding rules, design system, architecture docs, and safety invariants.]

## Phase 3 — Collect the Source
[Ask where the spec/prototype/brief lives and accept supported input types.]

## Phase 4 — Explore the Source
[Understand user-facing outcome, flows, data, dependencies, async work, and UI surfaces.]

## Phase 5 — Map to Integration Points
[Discover recipe files dynamically. Present recommended and not-needed recipes. Ask for confirmation.]

## Phase 6 — Load Relevant Recipes
[Read selected recipes. Present a sequenced execution plan. Ask for final confirmation.]

## Phase 7 — Execute
[Follow selected recipes in dependency order. Narrate progress. Stop on unresolved gaps.]

## Phase 8 — Quality Gate
[Run required typecheck, tests, lint, format, build, migration checks, or manual verification.]

## Phase 9 — Completion Summary
[Report branch, changes, flags/config, testing steps, known gaps, and next steps.]
```

Keep the final skill concise enough to be loaded during implementation. Put long examples, command references, or project inventories in a README or reference file instead of the main `SKILL.md`.

---

## Phase 5 — Preserve Key Orchestrator Invariants

Every integration orchestrator should include these rules unless the target project explicitly conflicts:

- **Dynamic recipe discovery:** List recipe files from the repository at runtime. Do not hardcode a stale catalog.
- **No code before confirmation:** Source exploration and mapping happen before implementation begins.
- **User-visible mapping:** Show why each recipe applies or does not apply.
- **Dependency-ordered plan:** Execute foundational changes before dependent work.
- **Stop on missing primitives:** If the prototype needs a UI component, service, permission, schema, or platform capability that does not exist, stop and ask.
- **Quality gate before completion:** Run the target project's validation checks and fix failures.
- **Completion report:** End with what changed, how to test, what remains off by default, and known follow-ups.

Project-specific invariants should be stronger than these generic rules. For example, if the target requires feature flags, migrations, audit logs, or accessibility checks, include them as mandatory execution rules.

---

## Phase 6 — Write Supporting README

If creating a new skill directory, also write a `README.md` that explains:

- What the skill builds
- When to use it
- What inputs it needs
- The generated orchestrator's phase model
- How it relates to integration-point recipe skills
- What files it usually creates or updates
- The checks to run before considering the generated orchestrator ready

Keep the README instructional, not a copy of the whole `SKILL.md`.

---

## Phase 7 — Verify the Result

Before finishing:

- Confirm the skill frontmatter has a lowercase kebab-case `name`.
- Confirm the description says both what the skill does and when to use it.
- Confirm file references are accurate.
- Confirm the orchestrator does not hardcode integration-point filenames unless the target project intentionally has a fixed set.
- Confirm the generated workflow has explicit user confirmation before implementation.
- Confirm the README describes the new skill rather than the feature being integrated.

End by telling the user which files were created or updated and any assumptions baked into the generated orchestrator.
