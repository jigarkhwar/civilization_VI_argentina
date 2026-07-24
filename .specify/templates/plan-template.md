# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]

**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command; its definition describes the execution workflow.

## Summary

[Extract from feature spec: primary requirement + technical approach from research]

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Languages/Formats**: [SQL, XML, Lua, DDS/art definitions, or N/A]

**Civilization VI Systems**: [database tables, modifiers, events, UI contexts, or NEEDS CLARIFICATION]

**Game/Expansion Baseline**: [current game version; Rise and Fall + Gathering Storm required;
no other DLC]

**Manifest/Load Order**: [affected Argentina.modinfo actions and ordering, or N/A]

**Validation**: [static checks, disposable database checks, in-game scenarios, logs, save/reload]

**Target Platform**: [Civilization VI platform/build and ModBuddy requirements]

**Compatibility-Sensitive IDs**: [existing IDs touched, or None]

**Player/Save Impact**: [observable gameplay or serialized-state impact, approval status, or None]

**Assets/Dependencies**: [base game, Rise and Fall, Gathering Storm, or repository assets only;
new dependencies require approval]

**Alternative-Mod Comparison**: [closest baseline from docs/DesignDifferentiation.md, deliberate
overlap, mechanical difference, and balance tradeoff]

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- **Compatibility and saves**: PASS only when game/expansion assumptions, stable identifiers,
  player-visible behavior, and save impact are declared; approval is recorded where required.
- **Native systems first**: PASS only when standard database tables and `Modifiers` are used where
  capable; every Lua, custom UI, dependency, or custom asset choice documents the native option gap.
- **Cross-layer integrity**: PASS only when manifest actions, load order, identifiers, localization,
  art links, and layer ownership are mapped for every affected runtime file.
- **Validation includes the game**: PASS only when applicable static checks and concrete in-game
  scenarios cover setup, Civilopedia, localization, mechanics, logs, and save/reload behavior.
- **Focused and reversible**: PASS only when the plan represents one coherent change and records
  every constitutional exception in Complexity Tracking.

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit-plan command output)
├── research.md          # Phase 0 output (/speckit-plan command)
├── data-model.md        # Phase 1 output (/speckit-plan command)
├── quickstart.md        # Phase 1 output (/speckit-plan command)
├── contracts/           # Phase 1 output (/speckit-plan command)
└── tasks.md             # Phase 2 output (/speckit-tasks command - NOT created by /speckit-plan)
```

### Source Code (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this feature. Delete unused options and expand the chosen structure with
  real paths (e.g., apps/admin, packages/something). The delivered plan must
  not include Option labels.
-->

```text
Argentina.modinfo
Gameplay/
Text/
├── en_US/
└── ru_RU/
UI/
Art/
Tests/
```

**Structure Decision**: [Document the selected structure and reference the real
directories captured above]

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., event-driven Lua mechanic] | [native-system capability gap] | [why Modifiers cannot express it] |
| [e.g., identifier replacement] | [required compatibility change] | [why the shipped ID cannot remain] |
