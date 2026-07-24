---

description: "Task list template for feature implementation"
---

# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`

**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, contracts/

**Validation**: Include all applicable static and in-game validation tasks from the specification.
Gameplay validation with a new save and save/reload is mandatory; unavailable manual checks remain
explicit handoff tasks and MUST NOT be marked complete.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- **Manifest**: `Argentina.modinfo`
- **Gameplay**: `Gameplay/`
- **Localization**: `Text/<locale>/`
- **Custom UI behavior**: `UI/`
- **Visual assets**: `Art/`
- **Offline validators and fixtures**: `Tests/`

<!--
  ============================================================================
  IMPORTANT: The tasks below are SAMPLE TASKS for illustration purposes only.

  The /speckit-tasks command MUST replace these with actual tasks based on:
  - User stories from spec.md (with their priorities P1, P2, P3...)
  - Feature requirements from plan.md
  - Entities from data-model.md
  - Endpoints from contracts/

  Tasks MUST be organized by user story so each story can be:
  - Implemented independently
  - Tested independently
  - Delivered as an MVP increment

  DO NOT keep these sample tasks in the generated tasks.md file.
  ============================================================================
-->

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Establish the focused files and validation fixtures required by the plan

- [ ] T001 Confirm Rise and Fall + Gathering Storm baseline, differentiation review, and approvals
- [ ] T002 Create focused runtime files in [exact Gameplay/Text/UI/Art paths]
- [ ] T003 [P] Create offline validation fixtures in Tests/ when required

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

Examples of foundational tasks (adjust based on your project):

- [ ] T004 Define stable database types and identifiers in Gameplay/[file].sql
- [ ] T005 [P] Add synchronized localization keys in Text/[locale]/[file].xml
- [ ] T006 Register runtime files and load actions in Argentina.modinfo
- [ ] T007 [P] Add reusable art or icon references in Art/[file] when required
- [ ] T008 Document native Modifier choices and any approved Lua capability gap

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - [Title] (Priority: P1) 🎯 MVP

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Validation for User Story 1

- [ ] T009 [P] [US1] Add applicable offline validator or fixture in Tests/[file]
- [ ] T010 [US1] Define the in-game scenario and expected log/save evidence in [quickstart path]

### Implementation for User Story 1

- [ ] T011 [P] [US1] Add gameplay definitions in Gameplay/[file].sql
- [ ] T012 [P] [US1] Add synchronized text in Text/[locale]/[file].xml
- [ ] T013 [US1] Register or order story files in Argentina.modinfo
- [ ] T014 [US1] Implement approved UI/Lua/art work in [exact path] when required

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - [Title] (Priority: P2)

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Validation for User Story 2

- [ ] T015 [P] [US2] Add applicable offline validator or fixture in Tests/[file]
- [ ] T016 [US2] Define the in-game scenario and expected log/save evidence in [quickstart path]

### Implementation for User Story 2

- [ ] T017 [P] [US2] Add gameplay definitions in Gameplay/[file].sql
- [ ] T018 [P] [US2] Add synchronized text in Text/[locale]/[file].xml
- [ ] T019 [US2] Register or order story files in Argentina.modinfo
- [ ] T020 [US2] Integrate with User Story 1 contracts without changing shipped identifiers

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - [Title] (Priority: P3)

**Goal**: [Brief description of what this story delivers]

**Independent Test**: [How to verify this story works on its own]

### Validation for User Story 3

- [ ] T021 [P] [US3] Add applicable offline validator or fixture in Tests/[file]
- [ ] T022 [US3] Define the in-game scenario and expected log/save evidence in [quickstart path]

### Implementation for User Story 3

- [ ] T023 [P] [US3] Add gameplay definitions in Gameplay/[file].sql
- [ ] T024 [P] [US3] Add synchronized text in Text/[locale]/[file].xml
- [ ] T025 [US3] Register or order story files in Argentina.modinfo

**Checkpoint**: All user stories should now be independently functional

---

[Add more user story phases as needed, following the same pattern]

---

## Phase N: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [ ] TXXX [P] Scan stable identifiers and localization references across Gameplay/ Text/ UI/ Art/
- [ ] TXXX Compare the completed player loop with docs/DesignDifferentiation.md and record overlaps
- [ ] TXXX Verify Argentina.modinfo registration, dependencies, and load order
- [ ] TXXX Verify no runtime reference requires DLC beyond Rise and Fall and Gathering Storm
- [ ] TXXX Run repository static validation and `git diff --check`
- [ ] TXXX Test with only this mod enabled and a new save
- [ ] TXXX Inspect Database.log, Modding.log, and Lua.log as applicable
- [ ] TXXX Verify setup, Civilopedia, localization, affected mechanics, and save/reload
- [ ] TXXX [P] Capture screenshots for UI or art changes
- [ ] TXXX Record game version, enabled expansions, results, and manual follow-up in review notes
- [ ] TXXX Run quickstart.md validation

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
  - User stories can then proceed in parallel (if staffed)
  - Or sequentially in priority order (P1 → P2 → P3)
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P2)**: Can start after Foundational (Phase 2) - May integrate with US1 but should be independently testable
- **User Story 3 (P3)**: Can start after Foundational (Phase 2) - May integrate with US1/US2 but should be independently testable

### Within Each User Story

- Stable identifiers and shared contracts before dependent gameplay or UI references
- Gameplay definitions before manifest/load-order integration
- Localization and art links before end-to-end in-game validation
- Applicable static validation before in-game validation
- Story complete before moving to next priority

### Parallel Opportunities

- All Setup tasks marked [P] can run in parallel
- All Foundational tasks marked [P] can run in parallel (within Phase 2)
- Once Foundational phase completes, all user stories can start in parallel (if team capacity allows)
- Offline fixtures and independent localization files marked [P] can run in parallel
- Independent gameplay and text files within a story marked [P] can run in parallel
- Different user stories can be worked on in parallel by different team members

---

## Parallel Example: User Story 1

```bash
# Prepare independent contracts for User Story 1 together:
Task: "Add gameplay definitions in Gameplay/[file].sql"
Task: "Add synchronized text in Text/[locale]/[file].xml"
Task: "Add applicable offline validator or fixture in Tests/[file]"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL - blocks all stories)
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Test User Story 1 independently
5. Deploy/demo if ready

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Test independently → Deploy/Demo (MVP!)
3. Add User Story 2 → Test independently → Deploy/Demo
4. Add User Story 3 → Test independently → Deploy/Demo
5. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Keep commits focused and green for each logical group
- Preserve shipped identifiers and keep localization and manifest references synchronized
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence
