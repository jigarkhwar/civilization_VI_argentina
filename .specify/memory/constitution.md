<!--
Sync Impact Report
- Version change: unratified template -> 1.0.0
- Modified principles:
  - Initialized I. Compatibility and Save Stability
  - Initialized II. Native Civilization VI Systems First
  - Initialized III. Cross-Layer Contract Integrity
  - Initialized IV. Validation Includes the Game
  - Initialized V. Focused, Reversible Delivery
- Added sections:
  - Technical and Content Constraints
  - Development and Release Workflow
- Removed sections: None; template placeholders were replaced.
- Templates:
  - ✅ updated: .specify/templates/plan-template.md
  - ✅ updated: .specify/templates/spec-template.md
  - ✅ updated: .specify/templates/tasks-template.md
  - ✅ reviewed, no update required: .specify/templates/checklist-template.md
  - ✅ not present: .specify/templates/commands/*.md
- Runtime guidance:
  - ✅ reviewed, already aligned: AGENTS.md
  - ✅ reviewed, no independent rules: CLAUDE.md
- Follow-up TODOs: None.
-->
# Argentina Civilization VI Mod Constitution

## Core Principles

### I. Compatibility and Save Stability (NON-NEGOTIABLE)
Database identifiers and localization keys that have shipped MUST remain stable across releases.
Every feature MUST declare its supported Civilization VI game version and expansion assumptions.
Changes to supported expansions, player-visible gameplay, or serialized state MUST be explicitly
scoped and approved before implementation. A change that cannot preserve existing saves MUST
document the break, its player impact, and its required major release.

Rationale: Civilization VI persists database identities and gameplay state in saves; seemingly
small identifier or rules changes can invalidate content or silently alter an existing campaign.

### II. Native Civilization VI Systems First
Gameplay mechanics MUST use Civilization VI database tables and standard `Modifiers` when those
systems can express the behavior. Lua MUST be introduced only for a documented capability gap and
MUST NOT move gameplay rules into UI code. Base-game assets MUST be referenced before custom art is
introduced; new dependencies and custom 3D or audio pipelines require explicit approval.

Rationale: Native systems load predictably, compose with other content, and are easier to inspect
and maintain than event-driven custom code or unnecessary asset pipelines.

### III. Cross-Layer Contract Integrity
`Argentina.modinfo` MUST be the authoritative registry for runtime files, load actions,
dependencies, and compatibility. Identifiers referenced across `Gameplay/`, `Text/`, `UI/`, and
`Art/` MUST match exactly, use the established Argentina prefixes, and have all required
localization and art links. Each runtime definition MUST have one clear owner, and gameplay rules
MUST remain outside UI code.

Rationale: The manifest and shared identifiers form a contract across independent game loading
layers; a mismatch can remove content without producing an obvious source-level failure.

### IV. Validation Includes the Game (NON-NEGOTIABLE)
Every change MUST pass `git diff --check` and all applicable repository static validation. Every
gameplay change MUST also be tested in Civilization VI with only this mod enabled and a new save.
That test MUST inspect `Database.log`, `Modding.log`, and `Lua.log` as applicable and verify setup,
Civilopedia, localization, affected mechanics, and save/reload behavior. UI or art changes MUST
include screenshots. Pull requests MUST record the tested game version, enabled expansions,
validation performed, and any validation that remains manual or unavailable.

Rationale: Syntax checks cannot reproduce Civilization VI load order, database integration,
modifier behavior, presentation, or persistence.

### V. Focused, Reversible Delivery
Each pull request MUST contain one coherent fix or feature, keep commits green, and exclude
opportunistic refactors. Work MUST branch from `main`; direct commits to `main`, pushes using
`--force`, and merge commits in pull-request branches are prohibited. Commits and pull-request
titles MUST follow Conventional Commits, and any necessary history rewrite MUST use
`--force-with-lease`.

Rationale: Small, reviewable changes isolate regressions and keep automated releases equivalent to
the player-visible change that was approved.

## Technical and Content Constraints

- Gameplay and localization MUST use focused SQL or XML files; Lua and UI XML are reserved for
  custom behavior and interface work, while DDS and Civilization VI art definitions own visuals.
- Files MUST use UTF-8, Unix line endings, and a final newline. XML and Lua use two-space
  indentation; SQL keywords use uppercase and continuation lines use two-space indentation.
- Database identifiers MUST use uppercase snake case and stable Argentina prefixes such as
  `CIVILIZATION_ARGENTINA`, `LEADER_SAN_MARTIN`, and `ARG_`; localization keys MUST stay
  synchronized with their gameplay references.
- The repository root MUST remain limited to manifests, project metadata, contributor guidance,
  and entry-point tooling. Runtime work belongs in `Gameplay/`, `Text/`, `UI/`, or `Art/`, and
  offline validators belong in `Tests/`.
- Proprietary game assets MUST NOT be copied into the repository when they can be referenced from
  the installed game. New dependencies, expansion support changes, custom asset pipelines, and
  release or publishing workflow changes require explicit approval.

## Development and Release Workflow

1. Scope the change before implementation. Substantial or ambiguous work MUST use a numbered
   `specs/NNN-*/` specification; small fixes MAY proceed without a specification when their scope
   and validation are unambiguous.
2. Plans MUST pass the Constitution Check before research and again after design. Any exception
   MUST be recorded in Complexity Tracking with the rejected simpler alternative and approval.
3. Implementation MUST preserve stable identifiers, keep localization and manifest entries in
   sync, and avoid unrelated cleanup.
4. Validation MUST satisfy Principle IV before the change is described as complete. Missing access
   to Civilization VI is a recorded manual validation item, not a passed test.
5. Pull requests MUST explain the player-visible result and compatibility impact. Release-producing
   `fix` or `feat` changes MUST merge individually into `main` after CI succeeds.
6. CI owns release tags and packages: `fix` increments patch, `feat` increments minor, and a
   breaking change increments major. Tags MUST match `vX.Y.Z`, exist only on `main`, and MUST NOT be
   deleted or reused. Steam Workshop publishing, when applicable, MUST use the same version.

## Governance

This constitution supersedes conflicting development guidance. Amendments MUST be proposed in a
reviewable pull request, include a Sync Impact Report, update affected templates and runtime
guidance, and state the semantic version rationale. Governance versions use semantic versioning:
MAJOR for removed or incompatibly redefined principles, MINOR for new principles or materially
expanded obligations, and PATCH for clarifications that do not change obligations.

Specifications, plans, task lists, and pull-request reviews MUST verify applicable constitutional
rules. A justified exception MUST identify the violated rule, why it is necessary, the simpler
alternative rejected, the compatibility risk, and the approving reviewer. Compliance MUST be
re-evaluated whenever design changes alter gameplay, persistent state, expansion support,
dependencies, or release behavior.

**Version**: 1.0.0 | **Ratified**: 2026-07-24 | **Last Amended**: 2026-07-24
