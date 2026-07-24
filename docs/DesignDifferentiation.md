# Argentina Design Differentiation Baseline

**Status**: Working design guardrails

**Reviewed**: 2026-07-24

**Scope**: Civilization, leader, unique components, and their core gameplay loop

## Purpose

This document records nearby Argentina mods so this project can offer a distinct reason to play.
It is a comparison baseline, not a blacklist. Historically necessary names and themes may overlap
when the design explains why they belong, gives them a materially different gameplay role, and
budgets their power rationally.

## Existing Workshop Baseline

### Leugi's Argentina Civilization

Source: [Steam Workshop item 910530559](https://steamcommunity.com/sharedfiles/filedetails/?id=910530559)

The description presents Argentina as a culture-and-production civilization with:

- a civilization ability that turns Great Works of Music into Production, adds music slots to
  Monuments, and awards Great Musician points from districts beside Pastures;
- a Gaucho replacing the Ranger, using light-cavalry and recon concepts and healing on Farms or
  Pastures;
- an Arrabal replacing the Neighborhood, with district-adjacency Production and Great Musician
  points;
- José de San Martín using mountain-crossing mounted units, kill-based Great General and Great
  Musician points, and a Granadero cavalry unit with a ranged attack;
- Julio Roca using border combat, tile acquisition after kills, and an Estancia Encampment tied to
  Forts, Pastures, expansion, and Military Engineers;
- Eva Perón using Theater Squares and Industrial Zones for population, Food, and Tourism;
- replacement of the Buenos Aires city-state with Montevideo.

### STR's Civs: Argentina

Source: [Steam Workshop item 2820652139](https://steamcommunity.com/sharedfiles/filedetails/?id=2820652139)

The description presents Hipólito Yrigoyen and Argentina through:

- Amenities from Campuses and Industrial Zones, a Food bonus when a city has both districts, and
  Suffrage-era Housing and Amenities;
- an era-based Paleontólogo, flexible Great Work slots in science buildings, and Fossils that
  produce Science and Tourism;
- a temporary Gaucho support unit that weakens nearby enemies and builds Estancias, Farms, or
  Pastures;
- an Estancia improvement with Farm, Pasture, and Plantation adjacency plus nearby mounted-unit
  movement;
- replacement of the Buenos Aires city-state with Ichma;
- required Rise and Fall, Gathering Storm, and Babylon Pack content. The Babylon dependency is a
  specific point this project will not repeat.

## Soft Differentiation Guardrails

The initial release SHOULD NOT reproduce the following packages without a written historical and
mechanical justification:

1. Great Works of Music, Great Musician points, and Pastures as one production/culture engine.
2. Paleontólogos, Fossil Great Works, and science-building display slots as the national engine.
3. A Gaucho and Estancia combined around Farms, Pastures, mounted movement, healing, or enemy
   debuffs.
4. Mountain-crossing cavalry paired with a ranged Granadero under José de San Martín.
5. Border combat that acquires tiles after kills, especially with a Roca or Conquista del Desierto
   framing.
6. Campus plus Industrial Zone combinations that turn flat land into Food and later add Housing or
   Amenities.
7. Theater Square plus Industrial Zone construction that directly grants population, Food, and
   Tourism.
8. Replacing the Buenos Aires city-state merely to make room for Argentina. This creates avoidable
   compatibility cost and is not a distinctive player-facing mechanic.

These are prompts to differentiate, not exclusions. `Gaucho`, `Estancia`, `Pampas`, `Patagonia`,
and other historically central names remain available. Reusing one requires the proposal to state:

- why the name or subject is historically important to this design;
- which existing implementation it resembles;
- how its unit class, timing, inputs, outputs, decisions, or counterplay differ;
- why the overlap improves the complete design more than a different component would;
- how its power is paid for elsewhere in the kit.

An isolated shared yield or name is acceptable. Copying the same trigger, reward, and supporting
components is not the default.

## Leader Direction

### Recommended: Manuel Belgrano

Belgrano is absent from both compared mods and supports a broader identity than another mounted
conqueror. His work connects the flag and a shared revolutionary identity, the Army of the North
and the Jujuy Exodus, Enlightenment ideas, commerce, and education. This supports a civic-economic
leader with a situational defensive dimension rather than another Pasture cavalry design.

Recommended design lane, subject to specification and balance testing:

- **Leader theme — Bandera de la Libertad Civil**: unity, morale, and recovery in defensive or
  liberation play; it MUST NOT duplicate San Martín's mountain movement or Roca's border seizure.
- **Economic theme — Consulado del Río de la Plata**: commercial connections fund civic or
  educational development. Prefer trade-route and Commercial Hub decisions over the existing
  Campus-plus-Industrial-Zone or Great Work engines.
- **Unique component candidates — Patricios, Consulado, or Cabildo**: favor infantry, commerce, or
  civic administration over a default Gaucho-and-Estancia pair. Historical fit and available base
  game assets MUST be verified before selection.
- **Player loop**: build a connected commercial state, convert a bounded part of that economy into
  civic development, and become difficult to break in a defensive war. Expansion by conquest is
  not the primary reward.

Relevant historical anchors:

- [Argentina.gob.ar: Belgrano, the May Revolution, Army of the North, Jujuy Exodus, and the flag](https://www.argentina.gob.ar/node/262529)
- [Argentina.gob.ar: creation and first raising of the flag](https://www.argentina.gob.ar/node/431401)
- [Argentina.gob.ar: Belgrano and the merchant-marine school](https://www.argentina.gob.ar/node/229680)

### Alternative: Guillermo Brown

Brown provides the largest mechanical gap: naval defense, the Río de la Plata, blockades, and
maritime trade are unused by the compared mods. He is a strong alternative if mechanical
distinctiveness matters more than choosing a civilian head of state.

Source: [Argentina.gob.ar: Admiral Guillermo Brown](https://www.argentina.gob.ar/armada/historia-naval/heroes-navales/almirante-guillermo-brown)

### Alternative: Juan Bautista Alberdi

Alberdi supports constitution-making, diplomacy, international agreements, immigration, and trade.
He offers an unusual government-and-diplomacy kit, but the design must explicitly accept a national
thinker and diplomat rather than a head of government as the leader.

Source: [Argentina.gob.ar: Juan Bautista Alberdi](https://www.argentina.gob.ar/noticias/juan-bautista-alberdi-sento-las-bases-para-organizar-la-patria)

### Later-Leader Candidates

- **Domingo F. Sarmiento** can support education, communications, journalism, and infrastructure,
  but a simple Campus or Science design would sit too close to Yrigoyen and the Paleontólogo kit.
- **Martín Miguel de Güemes** or **Juana Azurduy** can support frontier resistance and guerrilla
  warfare, but their strongest themes again approach Gaucho and rural cavalry territory. They fit
  better as later alternate leaders after the base civilization has a distinct non-Gaucho engine.

## Balance Policy

- The kit MUST have one primary economic or cultural engine, one situational leader reward, and at
  most one military component that exceeds its base-game replacement's normal power budget.
- A single trigger MUST NOT stack Food, Production, Science, Culture, Tourism, Housing, and
  Amenities without separate costs or caps.
- Scaling bonuses MUST be bounded per city, trade route, district, or era and evaluated at early,
  middle, and late-game milestones.
- A unique unit MUST identify the base unit it replaces, its timing, resource and maintenance
  costs, upgrade path, AI usability, and the base statistics traded for its special ability.
- A unique district, building, or improvement MUST identify both the opportunity cost of choosing
  it and the maximum realistic yield under ordinary play.
- The specification MUST compare the proposed loop with both Workshop baselines. Shared names are
  assessed by gameplay role, not rejected by name alone.
- The supported DLC baseline is exactly Rise and Fall plus Gathering Storm. Designs MUST NOT use
  gameplay definitions or assets that require the Babylon Pack, New Frontier Pass, Leader Pass, or
  another content pack.

## Proposal Checklist

Before accepting a leader or unique component, record:

- historical claim and source;
- closest Workshop analogue;
- shared names or themes and why they are retained;
- different trigger, reward, player decision, and counterplay;
- native Civilization VI implementation path;
- quantitative balance hypothesis and comparison target;
- confirmation that only Rise and Fall and Gathering Storm are required, plus compatibility impact.
