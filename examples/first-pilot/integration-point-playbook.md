# Integration point playbook: New internal admin page

Use this playbook when adding a bounded internal admin page to the existing admin surface.

## Purpose

This playbook handles internal pages used by support, operations, or engineering staff to inspect or act on existing product data.

## Use when

Use this playbook for requests like:

- add a page to list failed webhook deliveries
- add a page to search invoices
- add a page to inspect a user's recent activity

## Do not use when

Do not use this playbook when:

- the page is customer-facing
- the request introduces a new permission model
- the page needs a new domain API or data ownership decision
- the page performs bulk destructive actions

## Allowed scope

Agents may change:

- admin route registration
- one new admin page component
- page-local tests
- existing admin API client methods when the backend endpoint already exists

Agents may not change:

- global layout primitives
- role definitions
- database schema
- shared customer-facing components
- infrastructure or queue behavior

## Required locations

| Need | Location or pattern |
| --- | --- |
| Page implementation | `src/admin/pages/[Name]Page.tsx` |
| Route registration | `src/admin/routes.ts` |
| Admin API client | `src/admin/api.ts` |
| Tests | `src/admin/__tests__/[name].test.tsx` |

## Required contracts

- The page must render inside `AdminLayout`.
- The route must require the existing `support_admin` role.
- The page may read existing backend data but must not create new backend contracts.
- Retry actions must call an existing API endpoint and show success or failure state.

## Required safeguards

- Permissions: use the existing admin route guard.
- Validation: handle loading, empty, error, and retry failure states.
- Error handling: show a non-sensitive error message and keep the page usable.
- Logging/metrics: emit the existing admin action audit event when retry is clicked.
- Feature flag or rollout: keep the route hidden from navigation until product review signs off.

## Reuse expectations

Agents should prefer:

- `UserLookupPage.tsx` for route and layout shape
- `InvoiceSearchPage.tsx` for table, empty state, and error state patterns
- existing `adminApi` helpers for API calls

Agents should avoid:

- creating a new admin layout
- bypassing the route guard
- adding one-off fetch wrappers
- exposing raw internal error details

## Escalation triggers

The agent must stop and ask for review if:

- the requested role does not already exist
- the backend endpoint does not exist
- retry behavior needs a new queue, worker, or idempotency policy
- the page exposes customer PII not shown in existing admin pages
- product asks for bulk retry

## Validation checklist

Before completion, run:

- `npm run typecheck`
- `npm run lint`
- `npm test -- admin`

Manual review needed:

- product review for table columns and empty state copy
- engineering review for retry side effects and audit event payload

## Completion report

The agent should report:

- what changed
- which files were touched
- which validations ran
- whether the route is hidden from navigation
- any product or engineering review needs
