# Changelog

All notable changes to this repository are documented here.

This project follows a lightweight version of [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## Unreleased

### Added

- Simple engineering and product start paths in the README.
- Getting-started and implementation guides.
- Engineering templates for readiness, integration playbooks, change packages, agent instructions, validation policy, and escalation policy.
- Repo map and Mermaid diagrams for the operating model and product-to-production pipeline.
- Contribution, roadmap, security, issue template, pull request template, and documentation workflow scaffolding.
- `NL-SPEC.md` for installing a local Code-Left skills bundle in a target repo without cloning this repository.
- First-pilot worked example showing readiness assessment, playbook, change package, agent plan, and review learnings.
- `setup-code-left` skill for installing a local integrate orchestrator, first integration-point skill, product skills, and flow README.

### Changed

- Normalized agent terminology to avoid tying core docs to one tool.
- Replaced hardcoded tool-specific skill paths with `<agent-config>/skills/...`.
- Clarified that a change package is the agent-facing wrapper around product intent, and that agents should stop when required integration playbooks are missing.

### Fixed

- Replaced the empty misspelled docs index with `docs/README.md`.
- Fixed typos in existing docs.
