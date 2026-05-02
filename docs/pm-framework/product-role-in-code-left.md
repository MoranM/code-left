# What changes for the product role in Code-Left

This document describes how **product management** (and closely related roles such as product leadership) change when the organization adopts Code-Left. It is intentionally **product-centric** so we can later add a sibling doc for **UX and design** without rewriting the manifesto.

Code-Left is still **not** “PMs replace engineers.” It is: **product owns intent and bets**, **engineering owns the system of safe integration**, **agents own execution inside that system**—see [`code-left.md`](../../code-left.md). And all own value delivery to users and customers.

---

## 1. From vague intent to explicit bets

**Before:** Initiatives often arrive as themes, slides, or tickets that still need heavy interpretation.

**After:** Product frames work as **bets** on customer value: a clear hypothesis, who it is for, what will change for them, what success looks like, and what is explicitly out of scope.

**Implication:** The PM becomes accountable for **bet quality**—precision of the hypothesis and the evidence plan—not only for “having a roadmap.”

---

## 2. From handoffs to durable context

**Before:** Much of “why” and “what we know about users” lives in meetings, chats, and heads.

**After:** Product stewards **durable context** so agents and engineers do not reconstruct reality each time:

- **Where we want to get to** — strategy, goals, principles.
- **Who we are now** — the real product, segments, market, stakeholders, and evidence (qualitative and quantitative).
- **How we work** — routing, review, launch, escalation.

See [context-model.md](./context-model.md) and templates under [`../../templates/pm/`](../../templates/pm/).

**Implication:** PM main role continues to be understanding and reflecting the context needed to create good decisions and great products, but they also need to ensure they are **curating and linking** sources of truth (including analytics tools, CRM, support themes) and spending less time re-explaining the same background on every initiative.

---

## 3. From knowledge in heads to knowledge that compounds

This is true across every role in Code-Left, but it is especially important for product work: valuable context cannot stay trapped in conversations, memory, chat threads, or a few people’s instincts.

**Before:** A PM, designer, founder, support lead, or engineer “just knows” why a user behaves a certain way, why a constraint matters, or why a tradeoff was made.

**After:** That knowledge is written, linked, and reused so each new bet starts from a stronger base than the last one.

This does **not** mean documenting everything. It means turning the pieces of judgment that repeatedly shape decisions into durable artifacts:

- user and customer learnings,
- product principles and non-goals,
- current-product behavior and constraints,
- decision records and tradeoffs,
- analytics interpretations and caveats,
- workflow rules and escalation triggers.

**Implication:** Product becomes a steward of reusable product memory. Every bet should either use the existing memory or improve it. When an agent, PM, designer, or engineer discovers missing context, the system should get better—not just the current ticket.

---

## 4. From “requirements for engineers” to “intent that can drive a system”

**Before:** Requirements are optimized for a human engineer to interpret.

**After:** Product produces artifacts that are **structured enough** to drive implementation through templates, specs, and agent skills—without pretending PMs are architects.

**Implication:** PMs invest in:

- truly understand users and customers,
- sharper user journeys and scenarios,
- explicit non-goals,
- measurable success signals,
- clarity on behavioral change and risk.

Engineering still owns **how it is built safely**; product owns **all relevant content was there** when bet was developed AND shipped.

---

## 5. Faster learning with users—not faster chaos

The operating goal is **higher tempo of validated value**: more disciplined bets, shipped through a controlled path, with **earlier contact with real users** and **clearer readouts**—not shipping faster by lowering standards.

---

## 6. Collaboration shifts (same partners, different contract)

| Partner | What changes |
| --- | --- |
| **Engineering** | Less repeated “where does this go?” PM supplies intent shaped for the integration system; engineering supplies seams, rules, and gates. |
| **Design / UX** | *(Placeholder for a future doc.)* Product should already bring flows, states, edge cases, and non-goals so UX can focus on experience quality and cohesion—not rediscovering product truth from tickets. |
| **Go-to-market / support** | Earlier heads-up on bets that change behavior, messaging, or training needs. |

---

## 7. Skills and artifacts product should expect to use

In this repository:

- **map-product-context** — decide which context to add first.
- **build-product-brief** — draft or refine a bet brief.
- **assess-work-item-complexity** — route work by risk.
- **build-technical-spec** — engineering handoff when implementation is in scope.

Paths: [`../../skills/pm/`](../../skills/pm/).

---

## 8. What does *not* change

- Owning prioritization against strategy and constraints.
- Representing user and customer outcomes.
- Saying “no” and defending scope.
- Partnering on launch, messaging, and adoption.

---

## 9. Future: UX-specific companion

A follow-on document should cover:

- how designers participate in bet briefs and specs,
- design systems and agent-safe UI patterns,
- research synthesis into the “who we are now” layer,
- accessibility and quality bars as non-negotiables in the workflow doc.

Until that exists, treat this file as the **product** baseline and extend—not replace—it when UX guidance lands.
