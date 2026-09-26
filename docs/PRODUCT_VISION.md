# Product Vision: Steam, Commercial Release and Expansion Model

OpenTower is currently a hobby project, but the architecture should not prevent a later commercial release.

## Long-term distribution goal

A possible target is a commercial release on Steam once the game is stable, legally clean and fun enough to stand on its own.

Potential release path:

1. private development phase
2. closed/internal testing
3. public demo or limited playtest
4. Steam Coming Soon page
5. Early Access if appropriate
6. full release
7. optional expansions / DLC

No Steam dependency is required for the core game during early development.

OpenTower must also be fully standalone from SimTower: commercial builds should contain only OpenTower-owned code and assets and must not require a user's original `SIMTOWER.EXE`, graphics or sounds.

## Base game principle

The base game should already feel complete and worthwhile on its own.

Core features should include the essential tower-management loop:

- building floors and rooms
- offices, apartments, shops and basic services
- elevators and transport
- population and visitor simulation
- economy
- progression
- basic operating costs
- save/load
- statistics and management UI

Optional paid expansions should add meaningful new simulation layers rather than remove fundamental functionality from the base game.

## Example expansion: Utilities

A future Utilities expansion could add a much deeper infrastructure simulation:

- electricity demand per room
- transformers
- substations
- emergency generators
- batteries
- solar generation
- peak loads
- outages
- water demand
- water pressure
- pumps
- storage tanks
- wastewater
- infrastructure maintenance
- utility-related emergencies

The base game could model utilities as ordinary operating costs, while the expansion activates the detailed infrastructure layer.

## Other possible expansion themes

Examples only, not commitments:

- Security & Emergency
- Luxury Hotels
- Transportation & Parking
- Green Building / Sustainability
- Maintenance & Engineering
- Events / Tourism
- Mega Towers / Special Scenarios

## Technical principle: modular simulation systems

Expansion-capable systems should be optional modules rather than hard-coded special cases.

Conceptually:

```text
Simulation
├─ AgentSystem
├─ EconomySystem
├─ ElevatorSystem
├─ BuildingSystem
│
├─ ElectricitySystem      optional
├─ WaterSystem            optional
├─ EmergencySystem        optional
└─ OtherFeatureSystem     optional
```

The Core should expose stable interfaces so optional systems can subscribe to simulation events and add data without tightly coupling themselves to unrelated systems.

## Feature entitlements

Steam ownership checks, DLC entitlements and platform-specific APIs must remain outside the pure simulation core.

Preferred structure:

```text
OpenTower.Core
    does not know about Steam

OpenTower.Godot / Platform layer
    checks available features / entitlements

Feature configuration
    tells the Core which optional systems are enabled
```

This allows:

- non-Steam builds
- development builds
- tests with all features enabled
- future storefronts
- easier automated testing

## Repository strategy

The commercial game source can remain private.

Possible public repositories later could include selected material such as:

- modding SDK
- example mods
- save/file-format documentation
- public API documentation
- selected tools
- issue tracker / community documentation

The main game repository does not need to be public for a Steam release.

## Licensing strategy

Do not import GPL or unclear-license code into the commercial game repository without a deliberate licensing decision.

External projects can still be used for research, behavioral comparison and format documentation where appropriate.

See:

- `docs/LEGAL.md`
- `docs/REFERENCE_PROJECTS.md`

## Current status

This document describes a future direction only. The immediate priority remains the first playable OpenTower prototype.
