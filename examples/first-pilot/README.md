# First pilot example

This example shows the expected outcome of a small Code-Left setup.

The scenario is intentionally simple:

> Add an internal admin page that lists failed webhook deliveries and lets support staff retry one delivery.

The fake product already has internal admin pages, role-based admin access, a webhook delivery table, and a standard page pattern. That makes this a good first pilot because the change is useful, repeated enough to matter, and bounded by existing architecture.

## Files

| File | Purpose |
| --- | --- |
| [repo-readiness-assessment.md](repo-readiness-assessment.md) | Shows why "new internal admin page" was chosen as the first pilot. |
| [integration-point-playbook.md](integration-point-playbook.md) | Defines the safe seam for adding internal admin pages. |
| [change-package.md](change-package.md) | Wraps the product request as the agent-facing package for the pilot. |
| [agent-implementation-plan.md](agent-implementation-plan.md) | Shows the kind of plan an agent should produce before editing. |
| [review-learnings.md](review-learnings.md) | Shows how review findings improve the playbook. |

## How to read this example

Read the files in order. The flow is:

1. Choose a pilot change type.
2. Document the integration point.
3. Provide one real product spec or wrap it in a change package.
4. Ask the agent to map it to available playbooks before producing an implementation plan.
5. Feed review learnings back into the playbook.

This example does not include production code. It shows the operating artifacts that make production code safer to delegate.
