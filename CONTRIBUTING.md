# Contributing to AI FPGA Engineer

## Authorship

All repository changes are authored by AI coding agents. Humans define requirements and review, approve, or reject pull requests; they do not edit repository files by hand.

## Branches and reviews

- Never commit directly to `main`.
- Use a feature branch named for the area and task, such as `boards/pynq-z2-bringup` or `systems/retro-computer-fpga`.
- Submit changes through a pull request and include what changed, why, the exact verification performed, and any hardware/tool limitations.
- Keep project-specific changes in the owning repository. Update a submodule pin only to a reviewed revision and explain the represented source change.

## Verification

Run checks appropriate to the change and report exact commands and outcomes. For FPGA implementation work, this may include HDL lint, simulation, formal verification, synthesis, timing/resource analysis, bitstream generation, and physical-board tests. Do not state that a stage passed unless it ran successfully; distinguish simulated, synthesized, and physically verified behavior.

For documentation-only changes, check links and consistency with inspected sources. Do not add generated artifacts, proprietary binaries, or firmware without documenting their license and provenance.
