# Custom Toolchain: Assembler, Linker, and Emulator

This repository contains a complete, custom-built software toolchain for a described computer architecture. The project consists of an assembler, a static linker, and a CPU emulator, all developed from scratch in C++. It demonstrates a thorough understanding of the translation hierarchy, object file formats, and low-level instruction execution.

## Overview

The toolchain bridges the gap between human-readable assembly code and machine-executable instructions. It successfully handles the entire pipeline: parsing assembly instructions, managing symbol tables and relocations, linking multiple object files into a cohesive memory payload, and finally simulating the hardware to execute the program.

## Core Components

### 1. The Assembler
Translates custom assembly language source files (`.s`) into relocatable object files (`.o`).
* **Two-Pass Assembly:** Implements a multi-pass approach to correctly resolve forward references and compute memory offsets.
* **Symbol Table & Relocations:** Generates comprehensive symbol tables and relocation records for data and code sections, allowing external references to be resolved later by the linker.
* **Directives & Sections:** Fully supports section definitions (e.g., text, data, rodata) and assembler directives for data allocation and symbol exports/imports.

### 2. The Linker
Combines multiple object files into a single, executable memory image (hex format).
* **Section Merging:** Aggregates corresponding sections from different object files into contiguous memory blocks.
* **Symbol Resolution:** Resolves undefined external symbols by cross-referencing global symbol tables across all provided object files.
* **Relocation Patching:** Applies relocation rules to update machine code with absolute memory addresses based on user-defined memory placement constraints.

### 3. The Emulator
A virtual machine that simulates the processor and memory to execute the linked machine code.
* **Fetch-Decode-Execute Cycle:** Accurately simulates the CPU pipeline, decoding opcodes and updating internal processor states.
* **Hardware Simulation:** Simulates general-purpose registers, a status register, and the main memory space.
* **Memory-Mapped I/O & Interrupts:** Handles basic memory-mapped peripherals (such as terminal input/output) and simulates hardware/software interrupts.

## Technologies Used

* **Language:** C++ (Standard Template Library used for robust data structures).
* **Build System:** GNU Make.
* **Architecture:** Custom architecture specified by the project requirements (incorporating standard RISC/CISC concepts).

## Getting Started

### Prerequisites
* A standard C++ compiler (e.g., `g++`)
* `make` utility

### Building the Toolchain
Clone the repository and compile each component using the provided Makefile. Because the build targets are separated, you need to build them individually:

1. **Build the Assembler:**
   ```bash
   make
