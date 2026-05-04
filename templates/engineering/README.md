# Engineering templates

These templates help engineering teams turn repo knowledge into safe integration structure for coding agents.

Start with only three files. The optional templates are useful later, but they should not block the first pilot.

## Start with these three

| Template | Use when |
| --- | --- |
| [repo-readiness-assessment.md](repo-readiness-assessment.md) | Choosing the first repeated, low-risk change type to pilot. |
| [integration-point-playbook-template.md](integration-point-playbook-template.md) | Documenting one safe seam agents can use. |
| [change-package-template.md](change-package-template.md) | Packaging one real request so the playbook can be tested. |

## Simple setup flow

1. Fill the readiness assessment.
2. Pick one pilot change type.
3. Fill one integration-point playbook for that change type.
4. Fill one change package for a real request.
5. Run one agent-assisted implementation through the playbook.
6. Update the playbook based on where the agent guessed or got stuck.

## Use later

| Template | Use when |
| --- | --- |
| [agent-instruction-template.md](agent-instruction-template.md) | Turning a repeated playbook workflow into a reusable agent instruction set. |
| [validation-policy-template.md](validation-policy-template.md) | Formalizing quality gates across change types. |
| [escalation-policy-template.md](escalation-policy-template.md) | Formalizing when agents must stop for product, engineering, or architecture review. |

Use the optional templates only after the first pilot exposes repeated needs.
