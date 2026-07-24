# Feature Specification: [FEATURE NAME]

**Feature Branch**: `[###-feature-name]`

**Created**: [DATE]

**Status**: Draft

**Input**: User description: "$ARGUMENTS"

## User Scenarios & Testing *(mandatory)*

<!--
  IMPORTANT: User stories should be PRIORITIZED as user journeys ordered by importance.
  Each user story/journey must be INDEPENDENTLY TESTABLE - meaning if you implement just ONE of them,
  you should still have a viable MVP (Minimum Viable Product) that delivers value.

  Assign priorities (P1, P2, P3, etc.) to each story, where P1 is the most critical.
  Think of each story as a standalone slice of functionality that can be:
  - Developed independently
  - Tested independently
  - Deployed independently
  - Demonstrated to users independently
-->

### User Story 1 - [Brief Title] (Priority: P1)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently - e.g., "Can be fully tested by [specific action] and delivers [specific value]"]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]
2. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

### User Story 2 - [Brief Title] (Priority: P2)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

### User Story 3 - [Brief Title] (Priority: P3)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

[Add more user stories as needed, each with an assigned priority]

### Edge Cases

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right edge cases.
-->

- What happens when [boundary condition]?
- How does system handle [error scenario]?

## Requirements *(mandatory)*

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right functional requirements.
-->

### Functional Requirements

- **FR-001**: Mod MUST [specific player-visible capability, e.g., "make Argentina selectable"]
- **FR-002**: Mod MUST [gameplay rule, e.g., "apply the leader trait to eligible units"]
- **FR-003**: Players MUST be able to [key interaction, e.g., "inspect the trait in Civilopedia"]
- **FR-004**: Mod MUST [cross-layer contract, e.g., "register every gameplay file in the manifest"]
- **FR-005**: Mod MUST [localization requirement, e.g., "resolve every displayed text key"]

*Example of marking unclear requirements:*

- **FR-006**: Mod MUST apply the trade bonus to [NEEDS CLARIFICATION: domestic routes,
  international routes, or both?]
- **FR-007**: Mod MUST apply [NEEDS CLARIFICATION: exact bonus value and qualifying conditions?]

### Compatibility Requirements *(mandatory)*

- **COMP-001**: Supported Civilization VI game version: [version or NEEDS CLARIFICATION]
- **COMP-002**: Supported expansions and rulesets: Rise and Fall plus Gathering Storm; no other DLC
- **COMP-003**: Existing database identifiers affected: [None or exact identifiers]
- **COMP-004**: Save compatibility impact: [None, compatible migration, or documented break]
- **COMP-005**: Player-visible gameplay impact: [None or exact behavior and approval status]
- **COMP-006**: Manifest, localization, UI, and art contracts affected: [None or exact keys/files]
- **COMP-007**: Dependencies or custom asset pipelines: [None, or approved repository-owned asset
  work; external DLC beyond Rise and Fall and Gathering Storm is prohibited]

### Key Entities *(include if feature involves data)*

- **[Civilization/Leader/Trait]**: [What it represents and its player-visible attributes]
- **[Unit/Building/Modifier]**: [Its gameplay role and relationships to other database objects]

## Validation Evidence *(mandatory)*

- **Static validation**: [required syntax, schema, identifier, and workflow checks]
- **In-game scenarios**: [setup, Civilopedia, localization, mechanic, UI/art checks, or N/A with reason]
- **Logs to inspect**: [Database.log, Modding.log, Lua.log, or N/A with reason]
- **Persistence**: [new-save and save/reload checks, or N/A with reason]
- **Review evidence**: [tested game version, enabled expansions, screenshots for UI/art, manual follow-up]

## Historical and Gameplay Differentiation *(mandatory for civilization content)*

- **Historical basis**: [claim, source, and reason this subject belongs in the design]
- **Closest existing implementation**: [comparison from docs/DesignDifferentiation.md]
- **Deliberate overlap**: [shared names, leaders, themes, triggers, or None]
- **Distinct player loop**: [different inputs, decisions, outputs, timing, and counterplay]
- **Balance hypothesis**: [power budget, caps, opportunity costs, and base-game comparison target]

## Success Criteria *(mandatory)*

<!--
  ACTION REQUIRED: Define measurable success criteria.
  These must be technology-agnostic and measurable.
-->

### Measurable Outcomes

- **SC-001**: [Player outcome, e.g., "Argentina can be selected in every supported ruleset"]
- **SC-002**: [Mechanic outcome, e.g., "The bonus applies exactly once under each qualifying condition"]
- **SC-003**: [Compatibility outcome, e.g., "A save reload preserves all feature state"]
- **SC-004**: [Quality outcome, e.g., "All referenced text keys render in supported locales"]

## Assumptions

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right assumptions based on reasonable defaults
  chosen when the feature description did not specify certain details.
-->

- [Assumption about supported game version and expansions]
- [Assumption about scope boundaries, e.g., "Custom 3D assets are out of scope"]
- [Assumption about existing identifiers, saves, and localization coverage]
- [Dependency on a base-game table, modifier type, UI context, or referenced asset]
