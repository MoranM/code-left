# Change package: Failed webhook deliveries admin page

This package embeds the product spec in the shape the coding agent should use for integration mapping and implementation planning.

It should not be treated as a second source of truth. In this example, the product spec lives directly in this file.

## Source spec

- Mode: Embedded spec
- Type: Support ticket converted into embedded product spec
- Link or path: SUPPORT-1427
- Owner: Support operations

## Product spec

This embedded spec follows the canonical PM technical spec shape from [../../templates/pm/technical-spec-template.md](../../templates/pm/technical-spec-template.md).

### Context from the bet

- **Bet name and one-line value hypothesis:** Failed webhook delivery visibility will reduce support dependence on engineering for routine webhook failure investigation.
- **Primary users and non-goals:** Support admins need inspection and single-delivery retry. Bulk retry, new backend endpoints, and customer-facing UI are out of scope.
- **Links:** SUPPORT-1427

Support staff need a faster way to inspect failed webhook deliveries and retry a single delivery without asking engineering to query logs.

### Standalone product contract (v1)

- **Scope ownership:** Internal admin support surface owns the page.
- **Feature flag or rollout:** Route exists but is hidden from primary admin navigation until product review.
- **Primary entities and rules:** Failed webhook deliveries are read from existing backend data. Retry acts on one delivery at a time.
- **Ordering and defaults:** Show recent failed deliveries. Empty, loading, error, retry success, and retry failure states are required.
- **API or integration contracts:** Use existing `POST /admin/webhook-deliveries/:id/retry` endpoint.
- **Explicit v1 non-goals:** No bulk retry, no new backend endpoint, no new permission role, no customer-facing UI, no retry scheduling changes.
- **Requirement vs recommendation:** Acceptance criteria and functional requirements are mandatory for v1.

### User scenarios and testing

#### User story 1 - Inspect failed webhook deliveries (Priority: P1)

Support staff need a faster way to inspect failed webhook deliveries without asking engineering to query logs.

**Why this priority:** It removes a frequent manual support-to-engineering handoff.

**Independent test:** Open the hidden admin route as a support admin and verify the table states.

**Acceptance scenarios:**

1. **Given** failed deliveries exist, **When** a support admin opens the page, **Then** the table lists recent failed webhook deliveries.
2. **Given** no failed deliveries exist, **When** a support admin opens the page, **Then** an empty state is shown.

#### User story 2 - Retry one failed delivery (Priority: P1)

Support staff need to retry a single failed delivery from the row action menu.

**Why this priority:** It resolves common webhook delivery failures without engineering intervention.

**Independent test:** Trigger retry from one row and verify success and failure states.

**Acceptance scenarios:**

1. **Given** a retryable failed delivery, **When** a support admin clicks retry, **Then** the existing retry endpoint is called and success is visible.
2. **Given** retry fails, **When** the retry endpoint returns an error, **Then** failure is visible and the page remains usable.

### Edge cases

- No failed deliveries exist.
- Retry endpoint returns a validation error.
- Retry endpoint returns a transient server error.
- Delivery was already retried by another support user.

### Requirements

#### Functional requirements

The page should show:

- delivery ID
- customer name
- destination URL host
- failure reason
- last attempt time
- next retry time, if any
- retry status

- **FR-001:** A support admin MUST be able to open the page from the hidden admin route.
- **FR-002:** The page MUST show loading, empty, populated, and error states.
- **FR-003:** The table MUST list recent failed webhook deliveries.
- **FR-004:** Clicking retry MUST call the existing retry endpoint for one delivery.
- **FR-005:** Retry success and retry failure MUST be visible to the user.
- **FR-006:** The route MUST NOT be added to primary admin navigation yet.

#### Key entities

- **Webhook delivery:** Existing backend record representing one attempted webhook delivery.
- **Support admin:** Existing internal role allowed to inspect support admin pages.

### Success criteria

- **SC-001:** Support can inspect recent failed webhook deliveries without engineering help.
- **SC-002:** Support can retry one failed delivery through the existing retry endpoint.

### Definition of done

- [ ] Admin page tests cover loading, empty, populated, error, retry success, and retry failure states.
- [ ] Existing admin audit event is emitted when retry is clicked.
- [ ] Route is hidden from primary admin navigation.
- [ ] Product reviews table columns and empty state copy.

### Remaining clarifications (non-blocking)

- Confirm final empty state copy with product.
- Confirm whether failure reason should be raw enum or friendly label.
