# Map Integration Candidates

Use this skill when you want to find which parts of the codebase are good candidates for new integration-point skills.

It acts as an "Integration Point Scout": it scans a chosen scope, evaluates each major area for cohesion, coupling, extensibility, and reuse, then produces a prioritized report of patterns worth documenting.

## When To Use It

Run this before writing a new file in `.claude/skills/integration-points/`.

It is especially useful when:

- You are unsure which integration patterns are missing.
- A feature area has repeated implementation patterns that may deserve a recipe.
- You want to decide whether a module is stable and repeatable enough to document.
- You want a prioritized list of integration-skill gaps.

## What It Does

The skill follows a fixed six-phase workflow:

1. Agree on the analysis scope and report destination.
2. Map the high-level directory structure.
3. Check which integration-point skills already exist.
4. Read representative files across the chosen scope.
5. Rate each candidate area against quality signals.
6. Deliver the candidate report inline, to a file, or both.

The skill deliberately separates directory mapping from file reading. This keeps the first pass lightweight and helps the agent form a structural view before judging implementation details.

## Candidate Criteria

Strong candidates usually have:

- A focused responsibility.
- A consistent internal pattern across multiple instances.
- Low coupling to unrelated parts of the codebase.
- A clear extension path for adding new examples of the pattern.
- Reuse value across future features.

Weak candidates usually have scattered ownership, one-off logic, or dependencies spread across unrelated domains.

## Output

The final report includes:

- Scope analyzed.
- Existing integration-point skills found.
- Recommended candidates with quality ratings.
- Already-covered areas versus documentation gaps.
- Areas ruled out and why.
- Top-priority gaps to document first.

If a candidate is selected for follow-up, use the report as input to author a dedicated integration-point skill file in `.claude/skills/integration-points/`.
