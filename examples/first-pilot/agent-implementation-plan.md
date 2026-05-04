# Agent implementation plan: Failed webhook deliveries admin page

This is the kind of plan an agent should produce before editing code.

## Classification

**Selected integration point:** New internal admin page.

**Why:** The request adds a bounded internal page, uses an existing admin role, relies on an existing retry endpoint, and does not require new infrastructure or schema changes.

## Playbook fit

The playbook applies because:

- the page is internal-only
- route, layout, permission, and test patterns already exist
- retry is a single-row action
- the route can stay hidden from navigation

## Escalation check

No blocking escalation is required if the existing retry endpoint and audit helper are present.

Stop before editing if:

- `POST /admin/webhook-deliveries/:id/retry` is not implemented
- no existing admin audit event helper exists
- destination URL host parsing has no existing utility and policy is unclear

## Proposed changes

1. Read canonical examples:
   - `src/admin/pages/UserLookupPage.tsx`
   - `src/admin/pages/InvoiceSearchPage.tsx`
   - `src/admin/routes.ts`
   - `src/admin/api.ts`
2. Add `FailedWebhookDeliveriesPage`.
3. Register a hidden admin route guarded by `support_admin`.
4. Add admin API client methods only if existing endpoints already exist.
5. Add tests for loading, empty, populated, error, retry success, and retry failure states.
6. Run required validation.

## Validation

Run:

- `npm run typecheck`
- `npm run lint`
- `npm test -- admin`

## Completion report shape

Report:

- files changed
- route path
- whether navigation is hidden
- validation results
- open product copy questions
- engineering review needs around retry audit payload
