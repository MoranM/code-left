# Code Left

Skills, playbooks, and operating-model docs for helping companies become more AI-ready.

This repository is built around a simple premise: companies do not become AI-ready by giving everyone a coding agent and hoping for the best. They become AI-ready by making product intent clearer, engineering knowledge more explicit, and production change safer to delegate.

The core idea is **Code-Left**: engineering designs the system by which product intent enters production, so that coding agents can implement safely through known seams instead of relying on feature-by-feature human translation.

## What This Repo Is

This repo is a working library for teams that want to move from ad hoc AI usage to a repeatable AI-assisted delivery model.

It contains:

- Manifestos that define the operating model behind AI-assisted product development.
- Playbooks for turning product specs, prototypes, and POCs into production-ready changes.
- Templates for product briefs and technical specs.
- Skills and rules that encode repeatable workflows for agents.
- Course and training materials for PM and engineering collaboration.
- Early notes on infrastructure and platform capabilities needed for AI-native software delivery.

The goal is not to replace engineers with agents. The goal is to help engineering teams package their judgment into systems, rules, contracts, and workflows that make agent-assisted implementation safer and more scalable.

## Repo Description

An AI-readiness toolkit for companies: Code-Left manifestos, agent workflows, product-to-production playbooks, templates, and Cursor skills for making software delivery safer, more explicit, and more agent-friendly.

## The Core Thesis

AI coding agents make one thing obvious: the hard part of software delivery was never just typing code.

The hard part is integration:

- knowing where a change belongs
- understanding which existing patterns must be reused
- respecting architecture and domain boundaries
- adding the right observability and failure handling
- knowing when a change is safe, and when it needs escalation

In many organizations, that knowledge lives in engineers' heads. That does not scale when agents start participating in delivery.

This repo is about externalizing that knowledge into practical assets:

- architecture rules
- extension-point playbooks
- product change packages
- agent instruction sets
- validation checklists
- escalation policies
- repeatable skills and workflows

## Code-Left

`code-left.md` is the main manifesto for this repo.

It defines Code-Left as an operating model in which engineers stop being the default implementors of every feature and instead become the designers of the system that safely turns product intent into production code.

In this model:

- **Product owns product intent.**
- **Agents own implementation execution.**
- **Engineering owns the system of safe integration.**

That system includes extension points, contracts, templates, instruction layers, validation steps, policy checks, review triggers, and deployment guardrails.

The result is not less engineering. It is higher-leverage engineering.

## Who This Is For

This repo is intended for:

- Engineering leaders designing AI-assisted delivery workflows.
- Product leaders who want specs and prototypes to become more implementation-ready.
- Staff and principal engineers turning tribal knowledge into explicit integration systems.
- Platform teams building internal agent workflows.
- PM and engineer pairs experimenting with faster product-to-production loops.
- Companies trying to move from "we use AI tools" to "our system is AI-ready."

## What AI-Ready Means Here

An AI-ready company is not a company where agents can change anything.

An AI-ready company is one where common change types are explicit enough that agents can operate inside clear boundaries.

A repo is becoming AI-ready when:

- common change types have known integration points
- engineering rules are written down and reusable
- product specs include behavior, edge cases, non-goals, and acceptance criteria
- agents can identify the right playbook for a requested change
- tests and policy checks match the type of change being made
- human review focuses on risk and exceptions, not reconstructing missing context

A repo is not AI-ready when every task begins with repo archaeology, undocumented conventions, and a senior engineer manually catching the same mistakes over and over.

## Repository Contents - On going

### `code-left.md`

An earlier and more executive-oriented articulation of Code-Left.

Useful for introducing the idea to teams that need a concise strategic framing before going into the deeper manifesto.

### `skills/`



### `docs/`

Course materials for Level 5 product building with PM and engineer pairs.

These materials support the human side of the operating model: teaching teams how to collaborate around clearer product intent, stronger technical framing, and better delivery loops.

## Suggested Adoption Path

Start narrow, learn quickly, and expand only after the workflow is reliable.

1. Choose one high-repetition, low-risk change type.
2. Document the allowed integration point.
3. Create a change package template for product.
4. Create an agent instruction set for implementation.
5. Define required validation and review rules.
6. Run several real changes through the workflow.
7. Convert repeated mistakes into stronger rules, templates, or checks.
8. Expand to the next change type.

The point is not to fix the same ambiguity forever. The point is to platformize the answer.

## Principles

### Product intent should be structured

Specs should include scope, non-goals, invariants, user-facing behavior, acceptance criteria, and edge cases.

### Architecture should expose safe seams

Agents perform better when systems have clear extension points, stable contracts, and explicit ownership boundaries.

### Guardrails should be part of the workflow

Tests, schemas, lint rules, permission checks, observability, feature flags, and rollout controls are part of the execution model, not cleanup after implementation.

### Engineers should encode judgment

Engineering remains essential. The center of gravity moves from manually implementing every request toward designing the system that makes safe implementation repeatable.

### Agents should operate inside boundaries

Autonomy should be granted by change type, risk level, and validation strength. Some changes can be highly automated. Others require engineer review or architecture escalation.

## What This Is Not

This repo is not about:

- PMs replacing engineers
- agents coding from vague tickets
- unrestricted autonomy inside production repos
- faster prototyping without production discipline
- skipping architecture, review, tests, or rollout safety

If anything, Code-Left requires stronger engineering discipline because the path from product artifact to production becomes more direct.

## Future Direction

This repo can grow into a practical library of AI-readiness assets, including:

- integration playbooks by change type
- reusable Skills for product, design, engineering, and review workflows
- company readiness assessments
- spec and POC evaluation rubrics
- agent review checklists
- architecture rule templates
- production safety policies
- examples of AI-ready repo structures
- training material for PM and engineering pairs

## The Operating Agreement

Code-Left means engineering designs the system by which product intent enters production, so that coding agents can implement safely through known seams instead of relying on feature-by-feature human translation.

That is the shift:

- not less engineering
- different engineering
- higher-leverage engineering

