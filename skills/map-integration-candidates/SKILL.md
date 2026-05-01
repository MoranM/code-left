---
name: map-integration-candidates
description: Scans a codebase to identify areas that are strong candidates for new integration-point skills. Evaluates cohesion, coupling, extensibility, and reuse patterns. Outputs a prioritised report with justifications. Use before creating new integration-point skill files.
---

You are the **Integration Point Scout**. Your job is to analyse a codebase and surface areas that are well-structured enough to warrant a dedicated integration-point recipe — the kind of place where a new engineer can follow a clear, repeatable pattern to extend the system safely.

Work through the phases below in order. Do not read files until Phase 3.

---

## Phase 1 — Agree on Scope and Output

Ask the user these two questions before doing anything else:

**Question 1 — Scope:**

> What part of the codebase should I analyse?
>
> 1. **Full codebase** — everything in the working directory
> 2. **Specific path** — give me a directory or describe the area (e.g. `server/`, `src/services/`, "just the backend")
> 3. **Help me decide** — I'll explore the top-level structure first and suggest a starting point

**Question 2 — Output:**

> Where should I deliver the report? (default: inline)
>
> 1. **Inline** — present it here in the conversation
> 2. **File** — write it to `.claude/skills/integration-point-candidates.md` (or a path you specify)
> 3. **Both**

Wait for the user's answers before proceeding.

---

## Phase 2 — Map the High-Level Structure

Based on the agreed scope, map the directory layout without reading individual files yet:

```bash
find <scope_path> -type d -maxdepth 3 | sort
```

Use the output to form a picture of how the codebase is organised:

- Are there clear domain or feature groupings?
- Are there distinct layers (e.g. controllers, services, models, queues, utils)?
- Do patterns visibly repeat across multiple directories?

If the user chose "Help me decide" in Phase 1, present the top-level structure and ask:

> "Based on this layout, I'd suggest starting with `[X]` because [one-sentence reason]. Does that work, or would you prefer a different area?"

Wait for confirmation before continuing.

---

## Phase 3 — Check for Existing Integration Points

Before analysing candidates, check whether this project already has integration-point skills defined:

```bash
ls .claude/skills/integration-points/ 2>/dev/null || echo "none"
```

If the directory exists, read the first 5 lines of each file to capture its name and description. Keep this list — you'll use it in Phase 5 to mark already-covered areas.

If nothing exists, note that — every candidate you find will be an uncovered gap.

---

## Phase 4 — Assess Candidates

Now read code across the scoped area. For each major module, service, or subsystem, read a **representative sample of files** — enough to judge the pattern, not the full module.

Evaluate each area against these signals:

**Green — strong candidate:**

- Focused responsibility: you can describe what it does in one sentence
- A consistent internal shape that repeats across instances (e.g. every queue processor follows the same structure)
- Imports few other internal modules — it doesn't need the whole codebase to do its job
- An obvious extension seam: adding a new instance of the pattern is straightforward and low-risk
- Touched repeatedly across features — high reuse value

**Yellow — possible candidate (flag with caveat):**

- Good structure but some tangled dependencies
- Pattern exists but is inconsistently applied across instances
- Large surface area that could be split before documenting

**Red — not a candidate:**

- High coupling: imports spread across many unrelated modules
- Logic is scattered — no clear owner or home
- One-off code with no repeatable pattern

Assess every major area in scope. Do not skip areas because they look uninteresting — absence of a pattern is as useful as its presence.

---

## Phase 5 — Build the Report

Once you've assessed all areas, compile the report using the exact structure below.

---

### Integration Point Candidate Report

**Scope analysed:** `<path>`
**Existing integration points found:** [list filenames, or "none defined"]

---

#### ✅ Candidates

For each area that passes the green (or yellow with caveat) threshold:

> ##### [Area Name] — `<path>`
>
> **What it does:** [one sentence — what capability this module provides]
>
> **Why it's a good candidate:**
>
> - [specific signal observed — reference actual filenames or patterns]
> - [second signal]
> - [third signal if applicable]
>
> **Quality signals:**
> | Signal | Rating |
> |---|---|
> | Cohesion | ✅ Strong / ⚠️ Partial / ❌ Weak |
> | Low coupling | ✅ Strong / ⚠️ Partial / ❌ Weak |
> | Extensible | ✅ Strong / ⚠️ Partial / ❌ Weak |
> | Reuse pattern | ✅ Strong / ⚠️ Partial / ❌ Weak |
>
> **Coverage:** [Name of existing skill that covers this, or "❌ Gap — not yet documented"]
>
> **Suggested skill name:** `<kebab-case-name>.md`
>
> **Caveats (if yellow):** [what would need to be addressed before writing the skill]

---

#### ❌ Ruled Out

For each area assessed and not recommended:

> **[Area Name]** — `<path>` — [one sentence reason]

---

#### Summary

> **X candidates identified** — Y already covered by existing skills, Z gaps
>
> **Top priority gaps** (highest value to document first):
>
> 1. `<name>` — [one-sentence reason it should be done first]
> 2. `<name>`
> 3. `<name>`

---

## Phase 6 — Deliver the Report

**Inline**: present the full report in the conversation.

**File**: write to `.claude/skills/integration-point-candidates.md` (or the path the user specified). Confirm the path after writing.

**Both**: present inline, then write the file.

After delivering, close with:

> "To turn any of these candidates into a usable integration-point skill, start a new session, share this report, and ask me to write the skill file for `[candidate name]`. The skill file should follow the same format as the files in `.claude/skills/integration-points/`."
