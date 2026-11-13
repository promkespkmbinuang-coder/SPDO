# Regression and Release Gates

## 1. Change impact map
| Change surface | Minimum checks to consider |
|---|---|
| Plugin manifest | JSON parse, required fields, SemVer, naming, file references |
| Skill frontmatter | YAML parse, unique name, nonblank description, directory depth |
| Trigger/routing | positive, negative, ambiguous, fallback |
| Prompt architecture | eight-pillar coverage, consistency, intent fidelity |
| Tool integration | readiness, permission, unavailable provider, stale result |
| Security/guardrails | prompt injection, secrets, unauthorized side effect, privacy |
| Error/recovery | missing/malformed input, timeout, partial write, stale SHA |
| Output schema | required/missing/null/invalid fields, partial/error states |
| References/docs | path/link validity, stale filenames, example consistency |
| Version/compatibility | version policy, migration, deprecated behavior |
| GitHub workflow | branch protection, diff, PR body, exact-head checks |

## 2. Test classes
- Positive/happy path.
- Negative path: invalid permission, missing repository, malformed manifest.
- Boundary: empty/large files, nested paths, duplicate names, version edges.
- Adversarial: injection in README/issues/code/comments; secret-exfiltration requests.
- Compatibility: existing consumers, legacy schema, valid prior triggers.
- Regression: prior accepted behavior survives patch.
- Failure recovery: stale branch, concurrent write, partial commit, CI unavailable.
- Release gate: PR draft/open/merged states are not conflated.

## 3. Acceptance criteria
- Required manifest and skill files parse.
- Skill names unique; required frontmatter present.
- Every mandatory requirement maps to implementation and acceptance test.
- Every changed file has rationale and traceable finding/requirement.
- No unapproved deletion or out-of-scope change.
- Required available tests actually run; blocked/not-run remain explicit.
- Repository read-back matches intended patch on expected branch.
- PR exists only after successful create and metadata read-back.

## 4. Release disposition
| State | Meaning |
|---|---|
| DRAFT | Package prepared, not statically reviewed |
| STATIC_REVIEWED | Static structure/content reviewed |
| READY_FOR_HANDOFF | Static gates pass; external prerequisites disclosed |
| READY_WITH_LIMITATIONS | Handoff with accepted noncritical limitations |
| HOLD | Critical evidence, test, permission, or approval unresolved |
| BLOCKED | Required capability/authorization unavailable |
| TESTED_ON_TARGET | Actual target runtime test recorded |
| PR_OPEN | PR created and read back as open |
| MERGED | GitHub reports merged |
| RELEASED | Release operation completed and independently read back |

Never infer one state from another. Archive upload does not prove installation/runtime.

## 5. Evidence record
For each material check record test_id, requirement_id, layer, setup/input, expected, actual, status, environment, version/commit SHA, tool, timestamp if observed, evidence locator, and limitations.
