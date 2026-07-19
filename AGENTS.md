# Repository Guidelines

Civilization VI mod that adds Argentina as a playable civilization. Gameplay compatibility, stable database identifiers, localization, and save behavior are compatibility-sensitive.

> The sections above the divider describe the mod itself. The lightweight development and release process below applies to every contribution.

## Role

Maintain the Argentina mod with small, reversible changes. Prefer Civilization VI's database and modifier systems over custom Lua, reuse base-game assets until custom art is justified, and document assumptions about supported expansions.

## Stack

Gameplay and localization use SQL/XML; custom behavior and UI use Lua/XML; visual assets use DDS and Civilization VI art-definition formats. `Argentina.modinfo` is the mod manifest and load-order entry point. Project workflow tooling consists of GitHub Spec Kit, Copier, Bash, `gh`, and `jq`.

## Commands

```bash
# inspect changes
git status --short
git diff --check

# scan gameplay identifiers after content directories exist
rg "CIVILIZATION_ARGENTINA|LEADER_|ARG_" Gameplay Text UI
```

No automated game build or test runner exists yet. Add repeatable validation and packaging behind root-level commands such as `make validate` and `make package` when the first gameplay files are introduced.

## Structure

- `Gameplay/` — civilization, leader, units, buildings, traits, and modifiers in SQL/XML.
- `Text/<locale>/` — localized strings, for example `Text/en_US/` and `Text/ru_RU/`.
- `UI/` — Lua/XML interface extensions; keep gameplay rules out of UI code.
- `Art/` — icons, textures, models, and art definitions.
- `Tests/` — offline validators and fixtures when introduced.
- `specs/` — numbered Spec Kit feature specifications, plans, and task lists.
- `.specify/` — Spec Kit templates, extensions, presets, and workflow state.

Keep the repository root limited to manifests, project metadata, contributor documentation, and entry-point tooling. Prefer focused files such as `Gameplay/ArgentinaTraits.sql` over monolithic data files.

## Architecture

`Argentina.modinfo` registers files and load actions. Gameplay SQL/XML populates the game database; localization resolves referenced text keys; optional Lua reacts to gameplay or UI events; art definitions connect database entries to packaged assets. Keep identifiers stable across these layers and express mechanics through standard `Modifiers` before introducing event-driven Lua.

## Coding Standards

Use UTF-8, Unix line endings, and a final newline. Indent XML and Lua with two spaces; indent SQL continuations with two spaces and uppercase SQL keywords. Use descriptive PascalCase filenames. Database identifiers use uppercase snake case with stable prefixes, such as `CIVILIZATION_ARGENTINA`, `LEADER_SAN_MARTIN`, and `ARG_TRAIT_FEDERALISM`. Keep localization keys synchronized with gameplay identifiers.

## Test Model

Validate XML syntax and run SQL against a disposable Civilization VI-compatible database when practical. Every gameplay change also requires an in-game test with only this mod enabled and a new save. Inspect `Database.log`, `Modding.log`, and `Lua.log`; verify setup screens, Civilopedia entries, localization, affected mechanics, and save/reload behavior. Pull requests must record the game version, enabled expansions, validation performed, and screenshots for UI or art changes.

---

<!-- ===================================================================== -->
<!-- PROJECT DEVELOPMENT PROCESS                                           -->
<!-- ===================================================================== -->

## Boundaries

**Always:** branch from `main`, keep commits focused and green, preserve stable database identifiers, and maintain compatibility with declared Civilization VI expansions. `Argentina.modinfo` is the gameplay load-order and compatibility truth once added.

**Ask first:** new dependencies or upgrades, changes to supported expansions, observable gameplay or serialized-data behavior, editing another repository, custom 3D/audio pipeline work, and release or publishing workflow changes.

**Never:** force-push or commit directly to `main`, use merge commits in PR branches, commit broken code, perform opportunistic refactors outside scope, or copy proprietary game assets into the repository when they can be referenced from the game.

## Commits & PRs

- **One change per PR.** Keep a fix or feature focused enough to review and release independently.
- **Use Conventional Commits.** Examples: `feat(gameplay): add gaucho unit` and `fix(text): correct leader description`.
- **Use Spec Kit when useful.** Create `specs/NNN-*/` artifacts for substantial or ambiguous work. Small fixes do not require a specification or GitHub issue.
- **Intent, not path.** Do not add and then remove the same approach within one PR; squash exploratory churn before review.
- **Keep concerns separate.** Do not mix gameplay, documentation, and unrelated asset changes. Rebase branches and update remote history only with `--force-with-lease`.
- **Provide review context.** Explain the player-visible result, list validation, identify tested expansions, and attach screenshots for UI, icons, or art. Link an issue only when one exists.
- **Idiomatic code.** Follow SQL, XML, and Lua conventions already established here; avoid dead or duplicated definitions and exception-like control flow.

## Versioning & Releases

Every merged `fix` or `feat` produces a new release. Use semantic versioning for Git tags and GitHub Releases:

- `fix` increments the patch version: `v1.2.0` → `v1.2.1`.
- `feat` increments the minor version: `v1.2.1` → `v1.3.0`.
- A breaking change increments the major version: `v1.3.0` → `v2.0.0`.
- Documentation and workflow-only changes do not require a release unless explicitly requested.

Release directly from `main`; do not create release branches.

1. Merge one validated fix or feature PR into `main`.
2. Use `v0.1.0` for the first release; afterward, determine the next version from the latest `vX.Y.Z` tag.
3. Update the mod version in `Argentina.modinfo` once the manifest exists.
4. Create and push the new tag on the merge commit.
5. Publish an installable ZIP as a GitHub Release.
6. Publish the same version to Steam Workshop through ModBuddy when applicable.

Tags belong only on `main`. Never delete a published tag or reuse a version number. A release must contain exactly the fix or feature represented by its PR plus any required version metadata.
