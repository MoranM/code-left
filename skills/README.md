# Skills in this repository

Skills are markdown instruction sets for coding agents (and humans). Copy them into your agent config path if your tool expects a different layout (for example `.claude/skills/`).

## PM framework — bets and context

Every product addition is a **bet** on customer value. These skills help teams supply **where we want to get to**, **who we are now**, and **how we work** before implementation.

| Skill | Path | Use when |
| --- | --- | --- |
| **map-product-context** | [pm/map-product-context/](pm/map-product-context/) | Deciding which context sources to add first (docs, analytics, CRM, support, research). |
| **build-product-brief** | [pm/build-product-brief/](pm/build-product-brief/) | Drafting or improving a **bet brief** from the three context layers. |
| **assess-work-item-complexity** | [pm/assess-work-item-complexity/](pm/assess-work-item-complexity/) | Routing a bet or small work item (agent vs PM vs engineering). |
| **build-technical-spec** | [pm/build-technical-spec/](pm/build-technical-spec/) | Turning a bet brief into a **standalone** technical spec. |

Templates these skills reference: [../templates/pm/](../templates/pm/). Concept docs: [../docs/pm-framework/](../docs/pm-framework/).

## Integration readiness — engineering side of Code-Left

| Skill | Path | Use when |
| --- | --- | --- |
| **map-integration-candidates** | [map-integration-candidates/](map-integration-candidates/) | Scanning a codebase for strong integration-point candidates before writing recipe skills. |
| **build-integrate-skill** | [build-integrate-skill/](build-integrate-skill/) | Creating a project-specific **integration orchestrator** skill (similar to an `/integrate` flow) for your repo. |

## Adoption order (suggested)

1. **map-product-context** — know what context you have and what to add first.
2. Fill the three context layers from **templates/pm** (copy into your product repo as `docs/context/` or similar).
3. **build-product-brief** → **assess-work-item-complexity** → **build-technical-spec** for real bets.
4. In parallel, use **map-integration-candidates** and **build-integrate-skill** so engineering encodes safe seams for agents.
