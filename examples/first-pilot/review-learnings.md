# Review learnings: Failed webhook deliveries admin page

Use review learnings to strengthen the playbook, not just fix one implementation.

## What review found

- The agent used the correct route guard.
- The agent initially showed the full destination URL, including path and query string.
- Empty state copy needed product review.
- Retry audit event payload was missing the customer ID.
- Tests covered retry success but not "already retried by another support user."

## Playbook updates

Add these rules to the integration-point playbook:

- Destination URLs in admin tables should show host only unless a playbook explicitly allows full URL.
- Any row action that mutates backend state must emit an audit event with actor ID, customer ID, target ID, and action name.
- Product review is required for empty state copy on new admin pages.
- Retry tests must include the already-processed conflict case when the backend can return it.

## Template updates

No template change needed yet. The missing rules were specific to this integration point.

## Next pilot recommendation

Run one more internal admin page through the same playbook before expanding to background workers.
