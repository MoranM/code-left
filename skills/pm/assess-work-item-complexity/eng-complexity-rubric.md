# Engineering complexity rubric

Use this file to score **Eng complexity** (Low / Medium / High) for bet complexity assessment.  
Edit thresholds here as the team’s bar evolves; [`SKILL.md`](./SKILL.md) references this document.

## Low

Typical signals (any one cluster is enough; use judgment). Most bug fixes and small feature tweaks land here.

- UI-only or copy changes; reuses existing APIs and data shapes.
- No new persisted entities or migrations.
- No new background queues or long-running jobs.
- No authz model changes, no new integration with external providers.
- Blast radius: one surface, easy to flag off, trivial rollback.

## Medium

Typical signals:

- New or extended API surface, or meaningful service-layer changes.
- Schema change (additive migration, new table/columns) without large backfills.
- New or extended background job or async pipeline, or new model-assisted path with standard platform guardrails (adapt examples to your stack).
- Feature behind flag; moderate test and QA surface.
- One new integration (e.g. webhook, third-party API) with bounded scope.

## High

Typical signals (any strong signal can justify High):

- Authn/authz model changes, cross-tenant or permission semantics changes.
- Large or risky migrations (backfill, data rewrite, idempotency-sensitive cutover).
- Multiple coupled surfaces (client + API + worker + realtime) with tight ordering.
- New external provider on critical path, rate limits, or compliance-sensitive data.
- Performance or reliability sensitivity (hot paths, streaming, large payloads).
- **Ambiguity:** If the bet clearly needs repo exploration to size risk, default toward **Medium** until clarified; use **High** when unknowns imply large blast radius.

## Integration points (read before scoring)

**Do not hardcode integration types in this file.** The set of supported patterns changes as recipes are added or renamed under your repo’s integration-point folder (if any).

**Before you finalize Eng complexity**, do all of the following when an integration catalog exists (in order):

1. Read the repo’s documented catalog—often a skills README, agent README, or a section that lists **integration skills / integration points** (e.g. `.claude/skills/README.md` in repos that use that layout).
2. Scan the integration recipe folder (e.g. `.claude/skills/integration-points/` or your org’s path) — at minimum list the `*.md` files present and skim each file’s title/intro so you know what pattern it covers **today**.

If your repo has **no** such catalog or folder, skip the scan and write **"N/A — no integration catalog in repo"** in the assessment; rely on the Low/Medium/High bullets only.

When a catalog exists, then decide:

- **Clear integration mapping:** The bet clearly fits **one** documented pattern, or **a small, explicit combination** of patterns from that catalog (engineering has “prepared ground”: conventions, examples, and steps exist in-repo).
- **No clear integration mapping:** The work does not align with any current recipe; implementing it would require **a new** integration pattern or novel architecture **not** covered by those files.

For **intrinsic** Low / Medium / High, use the sections above (Low / Medium / High). Integration mapping **modifies** the final call as follows:

- **Mandatory escalation:** If your **intrinsic** Eng score is **not Low** (i.e. **Medium** or **High** by the Low/Medium/High bullets) **and** there is **no** clear integration mapping (a new pattern would be needed), the **final Eng complexity is High**. State both the intrinsic call and the escalation in the assessment.
- **Intrinsic Low:** Integration mapping is optional (e.g. copy-only or trivial reuse). Do not force an integration label if none applies.
- **Intrinsic Medium or High with** a clear mapping: score normally, but **cite** which recipe file(s) from the catalog the bet follows.

## Scoring rule

- Pick **High** if any High signal is clearly present **or** the **Mandatory escalation** under Integration points applies.
- Pick **Low** only if the work fits comfortably in Low and nothing material is unknown.
- Otherwise **Medium** — unless integration-point escalation forces **High**.
