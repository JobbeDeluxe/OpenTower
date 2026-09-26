# Reference Projects and Research Sources

This document tracks external projects and documentation that may help the OpenTower research effort.

The purpose is to learn from existing work without accidentally importing code or copyrighted game assets under incompatible or unclear terms.

## 1. OpenSkyscraper

Repository: https://github.com/fabianschuiki/OpenSkyscraper

OpenSkyscraper is an experimental open-source tower simulation inspired by SimTower.

Relevant characteristics:

- C++ codebase
- GPL-2.0 licensed
- can read graphics, fonts and sounds from a locally supplied `SIMTOWER.EXE`
- contains prior work on parsing the old Windows executable/resources
- useful for studying architecture, resource loading and previously explored mechanics

### OpenTower usage policy

OpenSkyscraper is a **research/reference source first**.

Because its code is GPL-2.0, copying or deriving OpenTower code from it could impose GPL obligations on the resulting distributed work. Until OpenTower's final licensing strategy is chosen, do not copy OpenSkyscraper source code into OpenTower.

Safe working approach:

- study concepts and architecture
- document observed behavior
- independently implement equivalent functionality in C#
- keep notes about which external sources were consulted

If we later deliberately choose a GPL-compatible license for OpenTower, direct reuse can be reconsidered.

## 2. ConciliaTower

Repository: https://github.com/Jonahss/concilia-tower

ConciliaTower is a ground-up C + SDL2 reimplementation of SimTower.

According to its project documentation it:

- reimplements game mechanics from scratch
- studies a Ghidra decompilation and the YootTower code map
- reads bitmap/sprite and WAV resources from a user-supplied `SIMTOWER.EXE`
- supports original `.TWR` / `.TDT` tower save formats
- can compile to WebAssembly for browser use

This makes it especially valuable as a **behavioral and file-format reference**.

### License caution

At the time of review (2026-09-26), the repository does not expose a clear root license file for the project's own source code. Internal project notes indicate GPL is intended, but that is not the same as a published license grant.

Therefore:

- do not copy ConciliaTower source code into OpenTower
- use it as documentation/research unless a clear license is published
- do not copy game-media/binary artifacts from third-party repositories into OpenTower

## 3. YootTowerManagement / YootTower

Repository: https://github.com/YootTowerManagement/YootTower

Don Hopkins states that Yoot Saito provided him with a historical Yoot Tower code drop for archival and academic study.

The public repository documents that the archive includes:

- Windows Tower sources
- original Maxis SimTower sources
- later Tower SP / Tower DS material

The repository currently contains documentation and a code map, while the README states that the source itself is intended to be published after cleanup, review, approval and relicensing.

### OpenTower usage policy

Until the original source code is actually published under an explicit usable license:

- treat the code map and public documentation as research material
- do not assume the unpublished original source is available for reuse
- re-check the repository periodically before making licensing decisions

## 4. tower-docs

Repository: https://github.com/dfloer/tower-docs

Useful additional documentation for the SimTower save format.

Relevant material:

- partial `.TDT` format specification
- experimental Python readers
- documentation under CC BY-SA 4.0
- code under AGPL-3.0

This can help us build independent savegame import/export support without starting the file-format research from zero.

## Original SimTower data owned by developers/users

OpenTower will use locally owned SimTower data as **development research material only**. The shipping game should not depend on or import original graphics, sounds or other copyrighted game assets.

Potential research targets:

- NE executable resource table
- bitmap/sprite resources
- WAV resources
- `.TWR` / `.TDT` save files
- version detection

Important separation:

```text
OpenTower release
├─ OpenTower code
├─ OpenTower-owned graphics
├─ OpenTower-owned audio
└─ OpenTower-owned data

Local development research
└─ SIMTOWER.EXE / original installation
```

Original SimTower files must not be committed to this repository, bundled into OpenTower releases, or required to run the game.

Owning a copy of the original game is useful for local research, but does not make its graphics, sound or other copyrighted assets part of OpenTower.

## Current engineering strategy

For OpenTower the preferred approach is:

1. Build the C# simulation core independently.
2. Use SimTower itself and existing reimplementations to verify behavior.
3. Use documented file formats where useful.
4. Ship only original OpenTower graphics, audio, text and other assets.
5. Keep any original-file analysis tooling internal and separate from the game.
6. Do not build player-facing dependence on `SIMTOWER.EXE` or extracted original media.
7. Avoid copying source code from projects whose license would unintentionally constrain OpenTower.
8. Revisit the YootTower source project if/when the historical source is formally published under a suitable license.

This preserves flexibility while still taking advantage of decades of existing research.
