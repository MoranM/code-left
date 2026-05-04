# Repo readiness assessment: [repo or product area]

Use this template to choose the first Code-Left pilot. Keep the first pass short.

## Summary

**Repo or area:** [name/path]

**Assessment date:** [date]

**Recommended first pilot:** [change type]

**Why this pilot:** [one paragraph]

## Candidate change types

List repeated change types that might become integration points.

| Change type | Example request | Frequency | Risk | Existing pattern? | Candidate? |
| --- | --- | --- | --- | --- | --- |
| [type] | [example] | [low/med/high] | [low/med/high] | [yes/partial/no] | [yes/no] |

## Best first pilot

**Chosen change type:** [type]

**Why it is a good first pilot:**

- [reason]
- [reason]
- [reason]

**Existing examples to study:**

- [file/path or link]
- [file/path or link]

## Current readiness

| Area | Status | Notes |
| --- | --- | --- |
| Product intent is usually clear | [yes/partial/no] | [notes] |
| Existing implementation pattern is consistent | [yes/partial/no] | [notes] |
| Safe files and modules are known | [yes/partial/no] | [notes] |
| Required validations are known | [yes/partial/no] | [notes] |
| Escalation triggers are known | [yes/partial/no] | [notes] |

## Gaps before the pilot

List only gaps that must be resolved before running one real change.

- [gap]
- [gap]

## Pilot success criteria

The pilot succeeds if:

- the agent can classify the change type correctly
- the playbook tells the agent where to integrate
- required validations are clear and runnable
- review focuses on risk and exceptions, not rediscovering basic repo rules
- any missing rules are captured back into the playbook
