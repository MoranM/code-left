# Context model for bets

This document defines what belongs in each context layer, what does not, and how agents should use them.

## Why three layers

Implementation risk is not the only risk. Bets also fail when:

- The team forgets **strategy** (builds the wrong thing).
- The team forgets **reality** (builds against an imagined product or user).
- The team forgets **process** (handoffs, review, and evidence standards are unclear).

Splitting context into three layers keeps each file focused and reusable.

---

## 1. Where we want to get to

**Purpose:** Answer *why* a bet fits the direction of the company and product, and what success means in strategic terms.

**Belongs here**

- Product thesis, positioning, and non-goals (“what we are not”).
- Company and team goals relevant to the product area.
- Naming, tone, and brand constraints if they affect product behavior or copy.
- Principles that should constrain many bets (privacy posture, quality bar, markets you serve).

**Does not belong here**

- Screen-by-screen behavior of the current app (that is “who we are now” or the bet brief).
- API or schema design (that is a technical spec).

**How agents should use it**

- Ground the bet’s promise and out-of-scope section in this layer.
- When strategy and evidence conflict, flag the tension instead of hiding it.

---

## 2. Who we are now

**Purpose:** Describe the **current** product and its world: what exists, who uses it, what the market expects, and what you have learned.

**Belongs here**

- Major surfaces, flows, and constraints of the **shipping** product.
- Customer and user segments, stakeholders, and competitive landscape at a useful level of detail.
- Evidence: summaries of findings and **links** to sources (analytics, research repository, support taxonomy, CRM notes, interview highlights).
- For **live systems** (PostHog, Google Analytics, Amplitude, Mixpanel, warehouse dashboards): do not paste full exports into this file unless your policy allows it. Prefer: tool name, link or workspace, key dashboards or saved reports, segment definitions, known caveats, **who may interpret** the data, and a link to a living analytics context artifact where reusable interpretation compounds.

**Does not belong here**

- The bet itself (use a bet brief).
- Implementation instructions (use a technical spec).

**How agents should use it**

- Treat this layer as the default **evidence** anchor for problem, user, and success signals.
- If the team lists analytics as a source, the agent should first look for the **living interpretation** of that source (for example `analytics-context.md`), then **query or request** only the narrow current numbers the bet depends on. Cite the tool, view, segment, and date range—not stale snapshots unless labeled as such.
- If a bet-specific analytics readout teaches something durable, add or propose a row back into the analytics context artifact. Otherwise the knowledge stays in the PM’s head and the next bet starts from scratch.

---

## 3. How we work

**Purpose:** Define the **operating system** for bets: how ideas become briefs, how complexity is assessed, what artifacts are required, and when to escalate.

**Belongs here**

- Required artifacts per bet tier (small fix vs larger bet).
- Owners for product, design, engineering, analytics, compliance as relevant.
- Review and launch policy (feature flags, QA, approvals).
- How unknowns are marked (`[UNKNOWN]`, `[NEEDS CLARIFICATION]`) and resolved.

**Does not belong here**

- Long narrative history of the company (a short link section is enough).

**How agents should use it**

- Follow this layer for **order of operations** and **stop points** (when to ask a human, when to require engineering review).

---

## Flexibility for different org sizes

**Small team**

- One markdown file per layer, maintained weekly, may be enough.

**Larger org**

- Many files per layer are fine. Add a **context source inventory** (see [`../../templates/pm/context-source-inventory.md`](../../templates/pm/context-source-inventory.md)) so agents know which files and tools apply to which product area.

**Minimum viable context**

- If a layer is missing, the agent should say so explicitly and still produce the best possible bet with `[UNKNOWN]` markers—not invented facts.
