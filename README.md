# OpVal: A Metadata-Based Validation Framework for RISC-V Opcodes and Traces
_...An upcoming open tool for validating, tracing, and debugging RISC-V opcode specifications with CI support. The project is currently in its initial phase of research and exploration, focusing on understanding existing tools and frameworks, studying historical efforts, and identifying gaps to address._

---

### 🧱 Foundational Work & Upstream Contributions

This project builds on significant prior work and contributions that I have made to the [riscv-opcodes](https://github.com/riscv/riscv-opcodes) repository, which forms the foundational groundwork for `OpVal`.

**🔧 Contributions include:**

- Refactored and optimized parser logic for opcode ingestion.
- Introduced shared utilities and YAML artifact-generation scripts.
- Enhanced the CI/CD pipeline for faster, more reliable builds.
- Reduced lines of code (LOC) to improve readability and maintainability.
- Optimized the Makefile for streamlined execution and testing.
- Reviewed, fixed, and merged PRs from the wider community.
- Provided best-practice recommendations for structure and maintainability.
- Resolved a multi-extension dependency bug by relocating `hinval.vvma` and `hinval.gvma` to `rv_svinval_h`, ensuring instruction legality when both Svinval and H extensions are used. Also fixed a related parser error affecting output generation.

**📌 Notable Pull Requests & Commits:**

- [Parser Refactor & Logic Simplification](https://github.com/riscv/riscv-opcodes/pull/283#pullrequestreview-2361430186)
- [CI Speed-Up & YAML Loader Enhancements](https://github.com/riscv/riscv-opcodes/pull/318)
- [Makefile Optimizations](https://github.com/riscv/riscv-opcodes/pull/266)
- [YAML Cleanup & Validation Fixes](https://github.com/riscv/riscv-opcodes/pull/309)
- [Test Infrastructure & Coverage](https://github.com/riscv/riscv-opcodes/pull/292)
- [Build & Parser Adjustments](https://github.com/riscv/riscv-opcodes/pull/311)
- [Issue Fixes & Robustness Improvements](https://github.com/riscv/riscv-opcodes/pull/299)
- [All Commits](https://github.com/riscv/riscv-opcodes/commits?author=IIITM-Jay)
- [PR #297: Split `hinval.vvma` and `hinval.gvma` from `rv_svinval` to `rv_svinval_h`](https://github.com/riscv/riscv-opcodes/pull/297)

These contributions reflect a deep engagement with the RISC-V ecosystem and directly inform the design of `OpVal`.

---

## Overview

As RISC-V adoption increases globally—especially within European initiatives like EPI, CHIPS JU, and RISE—ensuring correctness and trust in custom opcodes, ISA extensions, and trace encodings is critical. OpVal addresses the lack of early validation tooling in the open-source chip toolchain by providing:

- A **metadata-based validation engine** for opcode definitions.
- **Trace log analyzers** for verifying architectural correctness.
- **CI-friendly integration** through command-line tools and GitHub Actions.
  
OpVal aims to improve developer confidence, reduce ISA-level bugs, and speed up RISC-V processor design and verification pipelines in both academia and industry.

## Key Features

- [x] Validate RISC-V opcode encodings (bit overlap, value fit, syntax correctness)
- [x] Detect argument mismatches in opcode metadata vs. argument lookup tables
- [x] Check representability of constants based on encoding width
- [x] Validate trace logs against expected execution patterns (planned)
- [x] Command-line and CI (GitHub Actions) support
- [x] Modular design to support custom instruction extensions

## Why OpVal?

Current RISC-V tools such as [riscv-opcodes](https://github.com/riscv/riscv-opcodes), [spike](https://github.com/riscv-software-src/riscv-isa-sim), and simulators focus on instruction decoding and execution, but **lack formal, early-stage validation of opcode metadata** and trace analysis. OpVal fills this gap by:

- Offering standalone validation outside simulation
- Enabling detection of design-time encoding conflicts
- Supporting continuous integration for ISA development workflows

## Project Roadmap

### Project status and details for Phase0 - [Research & Exploartion](https://github.com/users/IIITM-Jay/projects/1/views/1?pane=info)

| Phase | Focus Area                            | Key Deliverables                                                                 |
|-------|----------------------------------------|----------------------------------------------------------------------------------|
| Phase 0: Exploration & Research | Landscape review & gap analysis        | Study existing tools (e.g., riscv-opcodes, spike, Sail), identify missing validation layers, define test cases |
| Phase 1: Foundations         | Project setup & metadata parser           | Initialize repository, parse RISC-V YAML opcode metadata, set up base infrastructure |
| Phase 2: Core Validation     | Encoding validation engine                | Implement bitfield overlap detection, field width checks, value representability, basic structural errors |
| Phase 3: Argument Checks     | Argument-table and semantics checks       | Validate mapping correctness, missing argument keys, malformed entries |
| Phase 4: Trace Analysis      | Trace format support & analysis tools     | Design trace log parser, compare trace semantics with defined encodings |
| Phase 5: CI Integration      | GitHub Actions & CLI utility              | Add command-line interface, GitHub Action integration, improve UX and error messaging |
| Phase 6: Public Release      | Documentation, examples & outreach        | Provide documentation, usage examples, package v1.0 release, outreach for adoption |


## Use Cases

1. Validate opcode additions to `riscv-opcodes` or other YAML-based metadata repos
2. Trace log checking for debugging and conformance validation
3. Use in academic labs for teaching/custom ISA exploration
4.  Support for custom extensions in open hardware startups
5.  CI integration to enforce correctness in collaborative development

## Getting Started

> _Note: Installation instructions will be updated after the initial release._

### Prerequisites

- Python 3.9+ (as earlier versions are depreacted. See more about python versions [here](https://devguide.python.org/versions/)
- `pyyaml`, `click` (CLI framework), and optional dependencies for trace checking

### Install

```bash
git clone https://github.com/IIITM-Jay/opval
cd opval
pip install -e .
