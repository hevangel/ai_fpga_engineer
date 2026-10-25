# AI FPGA Engineer Agent Guidelines

## Role

This repository is the AI FPGA Engineer. The AI agent is the sole author of its code, documentation, data, and configuration; humans direct the work and review the resulting changes. Use [CONTRIBUTING.md](CONTRIBUTING.md) for the branch and pull request workflow.

The project's purpose is to help turn the hardware and software work in the sibling AI Engineer projects into FPGA-board implementations. Use [AI Hardware Engineer](https://github.com/hevangel/ai_hw_engineer) as the engineering-process reference: specify first, plan implementation and tests, implement incrementally, verify with independent evidence, and report limitations honestly. Do not copy its repository wholesale.

## Required reading

- Read this file and [README.md](README.md) before making changes.
- Read [docs/boards.md](docs/boards.md) before changing supported-board claims or adding a board profile.
- Read each board's profile, source project instructions, and manufacturer documentation before implementing or changing board-specific behavior.
- Read system-specific instructions before changing an integrated system.

## Ownership and submodules

- Keep this repository's FPGA-specific designs and board integrations here.
- Keep `ai_hw_engineer`, `ai_sw_engineer`, and board-support repositories independent; do not copy their trees into this repository.
- `snickerdoodle/` is the user's maintained Snickerdoodle source repository.
- `external/pynq4-snickerdoodle-pismasher/` is an external PYNQ4/Snickerdoodle/Pi Smasher project.
- Before editing any submodule, read its own `AGENTS.md` and contribution instructions. Make changes in that project's repository and update this repository's pin only after the source revision is reviewed.

## Engineering requirements

- Define target board model and revision, FPGA/SoC device, clocking, reset, IO standards, pin constraints, boot path, software interface, and unsupported behavior in a specification before implementation.
- Keep board constraints and configuration in the relevant board profile. Avoid board-specific assumptions in reusable design logic.
- Plan simulation, formal checks where applicable, synthesis, timing/resource review, and hardware bring-up before implementation.
- Record exact commands, tool versions, source inputs, board revision, measured results, and limits in reports. A successful synthesis or bitstream build does not establish physical-board correctness.
- Cite inspected source evidence for hardware capabilities and technical claims. Label user-provided information as such until independently confirmed.
- Keep generated builds, downloaded firmware, and proprietary tool output out of version control unless the repository's licensing and provenance rules explicitly permit them.
- Never claim a board is supported until reproducible implementation and relevant physical behavior have been verified.

## Repository organization

- `boards/<board>/` — board profile, constraints, bring-up steps, and board-specific evidence.
- `design/<design>/` — reusable FPGA design specifications, plans, RTL, verification, and reports.
- `systems/<system>/` — integration of FPGA designs with AI Hardware Engineer designs and AI Software Engineer software.
- `external/` — independently maintained dependencies included as submodules.
- `scripts/` — reproducible build, verification, and reporting utilities.

Use SystemVerilog for RTL unless a project specification requires another HDL. Keep RTL portable where practical and isolate vendor-specific IP, constraints, and tool flows behind documented board/system profiles.

## Workflow

- Work on a feature branch and merge through a reviewed pull request; never push directly to `main`.
- Follow [CONTRIBUTING.md](CONTRIBUTING.md) for verification and pull request reporting.
- Do not change submodule pins as routine cleanup.
- Do not publish hardware support claims without linked, inspected evidence.
