# Repo readiness assessment: Internal admin pages

## Summary

**Repo or area:** Example SaaS admin surface

**Assessment date:** 2026-05-04

**Recommended first pilot:** New internal admin page

**Why this pilot:** The product already has several internal admin pages with the same route, layout, permission, data-fetching, and test pattern. A new page is useful enough to repeat but bounded enough that an agent can implement through a documented seam.

## Candidate change types

| Change type | Example request | Frequency | Risk | Existing pattern? | Candidate? |
| --- | --- | --- | --- | --- | --- |
| New internal admin page | Failed webhook deliveries page | Medium | Low | Yes | Yes |
| New customer-facing workflow | Invite team member flow | Medium | Medium | Partial | Not first |
| New billing event handler | Handle subscription paused event | Low | High | Partial | No |
| New background worker | Retry failed exports | Low | Medium | Yes | Later |

## Best first pilot

**Chosen change type:** New internal admin page

**Why it is a good first pilot:**

- Admin pages already use a standard route and layout pattern.
- Existing role checks and audit logging can be reused.
- The change is visible to internal staff only.
- Validation can use existing page tests, API tests, and lint/type checks.

**Existing examples to study:**

- `src/admin/pages/UserLookupPage.tsx`
- `src/admin/pages/InvoiceSearchPage.tsx`
- `src/admin/routes.ts`
- `src/admin/__tests__/admin-pages.test.tsx`

## Current readiness

| Area | Status | Notes |
| --- | --- | --- |
| Product intent is usually clear | Partial | Internal requests usually define goal and fields, but not always edge cases. |
| Existing implementation pattern is consistent | Yes | Admin pages share route registration, layout, permissions, and tests. |
| Safe files and modules are known | Yes | Changes should stay under `src/admin/` and reuse existing API clients. |
| Required validations are known | Yes | Typecheck, admin page tests, API tests, lint. |
| Escalation triggers are known | Partial | Permission and audit requirements need to be written down. |

## Gaps before the pilot

- Document the required admin permission wrapper.
- Document when audit logging is required.
- List canonical admin page examples.

## Pilot success criteria

The pilot succeeds if:

- the agent classifies the request as a new internal admin page
- the agent uses the existing admin route and layout pattern
- the agent reuses existing webhook delivery APIs
- validation commands are clear and runnable
- review learnings are captured back into the playbook
