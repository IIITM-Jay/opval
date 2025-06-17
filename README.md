# OpVal: A Metadata-Based Validation Framework for RISC-V Opcodes and Traces
_...An upcoming open tool for validating, tracing, and debugging RISC-V opcode specifications with CI support. The project is currently in its initial phase of research and exploration, focusing on understanding existing tools and frameworks, studying historical efforts, and identifying gaps to address._

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
