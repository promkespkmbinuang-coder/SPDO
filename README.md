# SPDO — Skill Developer Orchestrator

This repository contains **SKILL DEVELOPER ORCHESTRATOR (SDO)**, a governed workflow for auditing, improving, testing, and preparing AI skills/plugins for release.

## Package
- `skills/skill-developer-orchestrator/SKILL.md` — main orchestration skill
- `skills/skill-developer-orchestrator/references/` — audit, GitHub change, regression, and release protocols
- `plugin.json` — plugin manifest
- `tests/acceptance-cases.json` — acceptance-case specification

## Operating principles
Evidence before claims; explicit capability and permission checks; preserve user intent; branch/PR workflow by default; regression-aware changes; no fabricated test results; fail closed on critical unknowns. Merging and release remain separate human-governed gates.

## Status
Version 0.1.0. Static source package. Runtime compatibility and target-platform acceptance tests must be performed in their respective environments.

## License
Apache-2.0 (see `LICENSE`).
