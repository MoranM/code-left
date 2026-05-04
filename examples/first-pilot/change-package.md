# Change package: Failed webhook deliveries admin page

## Goal

Support staff need a faster way to inspect failed webhook deliveries and retry a single delivery without asking engineering to query logs.

## Requested behavior

Add an internal admin page that lists recent failed webhook deliveries.

The page should show:

- delivery ID
- customer name
- destination URL host
- failure reason
- last attempt time
- next retry time, if any
- retry status

Support staff should be able to retry one failed delivery from the row action menu.

## Acceptance criteria

- A support admin can open the page from the hidden admin route.
- The page shows loading, empty, populated, and error states.
- The table lists recent failed webhook deliveries.
- Clicking retry calls the existing retry endpoint for one delivery.
- Retry success and retry failure are visible to the user.
- The route is not added to primary admin navigation yet.

## Non-goals

- No bulk retry.
- No new webhook delivery backend endpoint.
- No new permission role.
- No customer-facing UI.
- No changes to retry scheduling policy.

## Edge cases

- No failed deliveries exist.
- Retry endpoint returns a validation error.
- Retry endpoint returns a transient server error.
- Delivery was already retried by another support user.

## References

- Existing admin page pattern: `src/admin/pages/UserLookupPage.tsx`
- Existing table pattern: `src/admin/pages/InvoiceSearchPage.tsx`
- Existing retry endpoint: `POST /admin/webhook-deliveries/:id/retry`
- Internal support request: SUPPORT-1427

## Suspected integration point

New internal admin page.

This request fits the admin page playbook because it adds a bounded internal screen using existing admin layout, permissions, and backend APIs.

## Data and permissions

- Requires existing `support_admin` role.
- Destination URL should display host only, not full path or query string.
- Customer name may be shown because existing admin pages already expose it to support admins.
- Audit event is required when retry is clicked.

## Rollout notes

- Add the route but keep it hidden from primary admin navigation.
- Support lead will test the direct URL before navigation is added.
- Monitor retry error rate after launch.

## Open questions

- Confirm final empty state copy with product.
- Confirm whether failure reason should be raw enum or friendly label.
