# Security policy

Code-Left is primarily documentation, templates, and agent instruction material. Even so, teams may use these assets to shape operational workflows, so security and safety feedback is welcome.

## Supported content

Security review applies to:

- templates that could encourage unsafe production workflows
- agent instructions that could weaken review, validation, permissions, or rollout safety
- documentation that creates misleading guidance for production systems
- repository automation such as documentation checks

## Reporting a concern

If you find a security or safety issue, please avoid opening a public issue with sensitive details.

Report privately to the repository maintainer. If no private channel is listed for your fork or organization, open a minimal public issue that says you have a security concern and ask for a private contact path.

## Operational use

Before using these templates in production workflows:

- adapt them to your repo, architecture, and risk model
- define explicit validation and review gates
- keep agents inside documented integration points
- require human review for unclear permissions, data ownership, infrastructure, or rollout risk

These materials are a starting point, not a substitute for your organization's security review.
