# Board Inventory and Support Plan

This page records the hardware the user has identified for `ai_fpga_engineer`. Inventory is not a support claim: each board remains unverified here until a reproducible implementation and relevant physical behavior are documented.

## AMD PYNQ-Z2 (AUP PYNQ-Z2)

- **User inventory:** The user has an AMD PYNQ-Z2 board.
- **Identification:** AMD's official University Program page lists the product as **AUP PYNQ-Z2**, describes PYNQ as an AMD open-source project, and identifies TUL as the board partner. The page lists a Zynq-7000 XC7Z020-1CLG400C SoC. Confirm the physical board revision before writing constraints.
- **Official AMD source:** [AUP PYNQ-Z2 product page](https://www.amd.com/en/corporate/university-program/aup-boards/pynq-z2.html).
- **Support state:** Inventory only; no bitstream, software image, or physical test is claimed by this repository yet.

## AMD Kria KV260 Vision AI Starter Kit

- **User inventory:** The user has an AMD KV260 board.
- **Official product name:** AMD calls it the **Kria KV260 Vision AI Starter Kit**. The official product page describes the kit as a development platform for Kria K26 SOMs. Confirm the exact hardware revision and kit contents before selecting a build flow.
- **Official AMD sources:** [Kria KV260 product page](https://www.amd.com/en/products/system-on-modules/kria/k26/kv260-vision-starter-kit.html), [KV260 user guide](https://docs.amd.com/r/en-US/ug1089-kv260-starter-kit), and [KV260 product details](https://docs.amd.com/r/en-US/ds986-kv260-starter-kit/Product-Details).
- **Support state:** Inventory only; no bitstream, software image, or physical test is claimed by this repository yet.

## Snickerdoodle with Pi Smasher

- **User inventory:** The user has a Snickerdoodle with Pi Smasher.
- **Source ownership:** Use the user's [hevangel/snickerdoodle repository](https://github.com/hevangel/snickerdoodle) as the canonical Snickerdoodle source, configured for `snickerdoodle/`.
- **Pi Smasher project:** Configure [eexma67/pynq4-snickerdoodle-pismasher](https://github.com/eexma67/pynq4-snickerdoodle-pismasher) for `external/pynq4-snickerdoodle-pismasher/`.
- **Manufacturer page:** [krtkl Snickerdoodle product page](https://krtkl.com/snickerdoodle/). It describes the Snickerdoodle module and lists technical specifications for the snickerdoodle one and snickerdoodle black variants. Verify which module variant and revision you own before applying those specifications.
- **Independent board context:** The [Crowd Supply project page](https://www.crowdsupply.com/krtkl/snickerdoodle) provides the original campaign overview. SparkFun's [Pi Smasher product page](https://www.sparkfun.com/pismasher-single-board-computer.html) describes Pi Smasher as a Snickerdoodle baseboard. Use the user's repository and the exact hardware revision/manual for implementation details.
- **Support state:** Inventory only; submodule commits are not yet pinned in this checkout, and hardware bring-up has not been verified.

## Board profile checklist

Before describing a board as supported, create a profile under `boards/<board>/` that records:

1. Manufacturer, exact model, revision, and FPGA/SoC part, with source links.
2. Required toolchain and exact tested versions, including any licensing constraints.
3. Clock, reset, pin assignments, IO standards, memory, boot source, and external connectors.
4. Reproducible synthesis/implementation commands and the expected output artifacts.
5. Simulation and formal checks where applicable, plus timing and resource results.
6. Physical bring-up steps, tested peripheral/software behavior, evidence, and known limitations.

Keep vendor-specific constraints and generated output scoped to the relevant board profile. Do not commit proprietary downloads or generated binaries without checking their redistribution terms and recording provenance.
