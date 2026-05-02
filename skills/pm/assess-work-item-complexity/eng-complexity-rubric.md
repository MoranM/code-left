# Engineering complexity rubric

Use this file to score **engineering complexity** (Low / Medium / High) for a bet or work item.  
Edit thresholds as your team’s bar evolves; [`SKILL.md`](./SKILL.md) references this document.

## Low

Typical signals (clusters are indicative; use judgment). Many bug fixes and small UI tweaks land here.

- UI or copy changes that reuse existing APIs and data shapes.
- No new persisted entities or migrations.
- No new long-running jobs or materially new async pipelines.
- No authn or authz model changes; no new critical third-party integrations.
- Blast radius limited to one surface; easy rollback or feature isolation.

## Medium

Typical signals:

- New or extended API surface, or meaningful service-layer changes.
- Additive schema changes without large backfills.
- New or extended background jobs, or new model-assisted paths with existing platform guardrails.
- Feature behind a flag with moderate test and QA surface.
- One bounded third-party integration.

## High

Typical signals (any strong signal can justify High):

- Authn, authz, tenancy, or permission semantics changes.
- Large or risky migrations, backfills, or idempotent cutovers at scale.
- Multiple coupled surfaces (client, API, jobs, realtime) with tight ordering.
- New external provider on a critical path, strict rate limits, or compliance-sensitive data.
- Performance or reliability sensitivity on hot paths.
- **Ambiguity:** if sizing requires deep repo exploration and unknowns imply large blast radius, default toward **Medium** until clarified; use **High** when unknowns imply major production risk.

## Integration-point mapping (optional)

If your repository defines **integration-point playbooks** (for example under `.claude/skills/integration-points/` or another path your team documents):

1. List the recipe files that exist.
2. If the work maps clearly to one or a small combination of recipes, cite them and score engineering with that preparedness in mind.
3. If **intrinsic** engineering is Medium or High **and** there is **no** clear mapping to an existing pattern, treat that as **higher risk**: note **"No clear mapping — new pattern needed"** and bias routing toward engineering-owned workflow unless the team accepts explicit risk.

If your repo has **no** integration-point catalog, write **"N/A — no integration catalog in repo"** and rely on the Low/Medium/High bullets only.

## Scoring rule

- Pick **High** if any High signal is clearly present, or ambiguity implies unacceptable blast radius.
- Pick **Low** only if the work fits Low comfortably and nothing material is unknown.
- Otherwise **Medium**.
