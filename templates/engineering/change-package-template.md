# Change package: [name]

Use this template as the thin agent-facing wrapper around product intent.

The change package should not create a second source of truth. It should either link to the product spec or contain the product spec directly.

Use one of two modes:

- **Linked spec:** the product spec, PRD, ticket, prototype, bet brief, or technical spec lives elsewhere and this file links to it.
- **Embedded spec:** this file contains the product spec directly.

## Source spec

Use one mode.

- Mode: [Linked spec / Embedded spec]
- Type: [spec / PRD / ticket / prototype / bet brief / technical spec / other]
- Link or path: [required for linked spec; optional for embedded spec]
- Owner: [person/team]

## Product spec

Use this section only when the spec is embedded in this file. If the spec is linked above, replace this section with a short pointer such as: "See linked source spec."

When embedding the spec here, use the canonical PM technical spec shape in [../pm/technical-spec-template.md](../pm/technical-spec-template.md). Do not duplicate or fork that template in this file.
