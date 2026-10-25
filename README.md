# AI FPGA Engineer

> This repository is the FPGA engineer: its job is to help turn the hardware and software work in the AI Engineer projects into working FPGA-board implementations.

## Purpose

`ai_fpga_engineer` owns the FPGA implementation and board-integration work. It connects designs from [AI Hardware Engineer](https://github.com/hevangel/ai_hw_engineer) with software from [AI Software Engineer](https://github.com/hevangel/ai_sw_engineer), then targets the boards listed below. Board support means documented constraints, reproducible builds, host/firmware integration, and verification on the actual hardware; a source checkout or successful bitstream build alone is not proof that a complete system works.

The repository uses the AI Hardware Engineer's specification, planning, implementation, verification, and reporting discipline, adapted for programmable logic and board-level integration. Keep board-specific pinouts and constraints with the board profile, shared FPGA designs in `design/`, and system integrations in `systems/`.

## Hardware inventory

See [the board inventory and support plan](docs/boards.md) for sources, evidence, and the current support state.

| Hardware | Intended role | Current support state |
| --- | --- | --- |
| [AMD PYNQ-Z2 (AUP PYNQ-Z2)](https://www.amd.com/en/corporate/university-program/aup-boards/pynq-z2.html) | FPGA development and hardware/software integration | Owned by the user; support not yet verified in this repository |
| [AMD Kria KV260 Vision AI Starter Kit](https://www.amd.com/en/products/system-on-modules/kria/k26/kv260-vision-starter-kit.html) | K26 SoM development and hardware/software integration | Owned by the user; support not yet verified in this repository |
| [Snickerdoodle with Pi Smasher](https://krtkl.com/snickerdoodle/) | FPGA SoC module with Pi Smasher carrier/peripherals | Owned by the user; submodule paths are documented, support not yet verified |

## Repository structure

```text
ai_fpga_engineer/
├── AGENTS.md               — Instructions for AI agents
├── CONTRIBUTING.md         — Branch, verification, and review workflow
├── README.md               — Project purpose and entry points
├── .gitmodules             — Board-support submodule URLs
├── docs/                   — Board inventory and engineering conventions
├── boards/                 — Board profiles, constraints, and bring-up records
├── design/                 — Reusable FPGA implementations and verification
├── systems/                — Integrated hardware/software targets
├── scripts/                — Reproducible build and verification entry points
├── snickerdoodle/          — User-maintained Snickerdoodle source repository
└── external/               — External board-support dependencies
    └── pynq4-snickerdoodle-pismasher/ — PYNQ4 Snickerdoodle/Pi Smasher project
```

Board support and systems will be added incrementally. Empty directories are created with their first board profile or implementation rather than tracked as placeholders.

## Getting started

Initialize the board-support repositories when you need them:

```bash
git submodule update --init --recursive
```

Before starting a board implementation, read [AGENTS.md](AGENTS.md), the board profile, the source project's instructions, and the applicable vendor manuals. Record exact tool versions, board revisions, constraints, build commands, verification results, and known limitations.

## Scope boundaries

- Keep upstream and user-maintained source repositories as Git submodules; do not copy their trees into this repository.
- Treat the user's `hevangel/snickerdoodle` repository as the canonical Snickerdoodle source for this project, configured at `snickerdoodle/`.
- Keep `eexma67/pynq4-snickerdoodle-pismasher` under `external/` as an independently maintained dependency, configured at `external/pynq4-snickerdoodle-pismasher/`.
- Do not claim support for hardware until the build and relevant behavior are verified and reported on the physical board.
- Do not add proprietary binaries, firmware, or vendor-tool output unless licensing and provenance are documented.
