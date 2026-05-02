# PM framework: bets and context

This folder describes the **product** side of Code-Left: how teams turn ideas into **bets** on customer value, and how they give agents enough **context** to work safely and well.

## Core idea

Every product addition is a **bet**: a hypothesis that a change will improve value for customers or users. Good bets need good context—not more slides, but **clear, reachable sources of truth** that agents and humans can use together.

## Three context layers

Agents (and humans) do better when three kinds of context exist and are easy to find:

1. **Where we want to get to** — Vision, company and team goals, product-area strategy, principles, and why this work matters now.
2. **Who we are now** — The product as it actually works today, plus customers, users, market, stakeholders, constraints, and evidence (including analytics, support, sales, research).
3. **How we work** — The workflow from idea to bet to spec to implementation to observation and learning and so on: artifacts, owners, review gates, escalation, and when PMs, agents, or engineering own the next step.

See [context-model.md](./context-model.md) for detail.

For how the **product role** shifts (bets, context, collaboration)—and a stub for later **UX** expansion, see [product-role-in-code-left.md](./product-role-in-code-left.md).

## Bet brief vs technical spec

The **bet brief** (product intent) gathers the context needed to **evaluate the bet**: who it is for, the hypothesis, evidence, scope, and success signals—without turning into an engineering design. The **technical spec** gathers what is needed to **plan and build safely**: requirements, contracts, edge cases, and testable behavior an implementer can execute without re-opening the brief for every ambiguity.

## Templates

Canonical **reference** copies live under [`../../templates/pm/`](../../templates/pm/). Most products already have their own brief, PRD, or technical-spec shapes—use those as the working artifacts and treat Code-Left templates as a **gap check** and refinement guide, not a mandatory replacement. Teams typically:

- Copy templates into their own repo (for example `docs/context/`) when they lack a local shape, or
- Keep a single shared handbook and link paths in their agent skills, **or**
- Point skills at existing org templates and ask agents to map or suggest improvements against these reference files.

Start with **one file per layer** if that is all you have time for. Expand when bets keep failing for the same missing-context reason.

## Fast start

For a first pass, do **not** set up every template. Pick one real bet and give the agent:

1. Your existing brief, PRD, ticket, or rough notes.
2. Links or short notes for the three context layers: direction, current reality, and how work gets shipped.
3. Any known evidence or analytics view that matters for this bet.

Then use **build-product-brief** to tighten the bet, run a quick **assess-work-item-complexity** routing check, and only create new context files for gaps that will repeat across future bets.

## Full workflow

1. Run the skill **map-product-context** (see [`../../skills/pm/map-product-context/`](../../skills/pm/map-product-context/)) to decide what to add first.
2. Fill or link **where we want to get to**, **who we are now**, and **how we work**.
3. Use **build-product-brief** to draft or refine a **bet brief** (or your org’s equivalent) from those sources.
4. Use **assess-work-item-complexity** to route the bet (agent vs PM vs engineering).
5. Use **build-technical-spec** when you need an implementation-ready spec (using your org’s spec template when you have one).

## Relation to Code-Left engineering assets

The manifesto and engineering playbooks live in [`code-left.md`](../../code-left.md). Skills for integration seams and orchestrators live under [`../../skills/`](../../skills/). This PM framework supplies **intent and context**; engineering supplies **safe integration**.
