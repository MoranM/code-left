# Validation policy

Use this optional template when validation differs by change type or needs to be shared across playbooks.

## Baseline checks

Required for all changes:

- [command/check]
- [command/check]

## Checks by change type

| Change type | Required checks | Manual checks |
| --- | --- | --- |
| [type] | [checks] | [checks] |

## Observability requirements

Required logs, metrics, traces, analytics, audit events, or dashboards.

- [requirement]
- [requirement]

## Security and permissions checks

Checks for auth, roles, data access, secrets, PII, policy constraints, or compliance.

- [check]
- [check]

## Rollout checks

Checks for feature flags, migrations, backwards compatibility, staged launch, monitoring, and rollback.

- [check]
- [check]

## When checks fail

If a required check fails, the agent should:

1. Summarize the failure.
2. Fix failures that are clearly caused by its change.
3. Stop and report failures that are unrelated, flaky, blocked, or require policy decisions.
