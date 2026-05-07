# VHDL-RISC-Processor-Artix7
A hardware implementation of the 16-bit DI-RISC architecture, a custom register-load-store RISC processor. Developed in VHDL and deployed on a Xilinx Artix-7 FPGA, this project features a custom-coded instruction decoder, memory-mapped I/O, and a validated ISA for arithmetic and logical operations

# DI-RISC Processor Implementation on Artix-7 FPGA

## Project Overview
This project features the hardware implementation and verification of a **16-bit Register-Load-Store RISC architecture**, known as the **DI-RISC**. Developed as part of the "Programmable Architectures" curriculum at HAW Hamburg, the project focuses on designing central control logic and validating the processor through behavioral simulation and physical hardware deployment.

### Key Technical Specifications
* Architecture: 16-bit Register-Load-Store RISC
* Data/Instruction Width: 16-bit
* Registers: 8 general-purpose registers (R0-R7)
* Memory: 512-word Program Memory (PMEM) and 1024-word Data Memory (DMEM)
* Target Hardware: Xilinx Artix-7 FPGA (XC7A100T CSG324-1)

## Implementation Details

### 1. Control Unit Development
The core of the implementation involved developing the logic for the Instruction Decoder and Address Decoder within the `DIRISC_control_unit.vhd` module:
* **Instruction Decoder**: Designed to slice 16-bit machine code into functional bit fields (opgroup, opcodes, src, and dst).
* **Address Decoder**: Implemented memory-mapped I/O logic to distinguish between Data Memory access and I/O module access for switches and LEDs.

### 2. Instruction Set Architecture (ISA)
The processor supports four primary instruction types:
* **REGREG**: Arithmetic and logical operations performed between registers.
* **LOAD/STORE**: Data movement between the Register File and Memory/IO.
* **BRANCH**: Flow control via Program Counter (PC) offsets.

### 3. Machine Code Assembly
Machine code was manually assembled in `DIRISC_pmem.vhd` to perform specific hardware tasks:
* Sequential ALU data manipulations using internal registers.
* Reading input from hardware switches, performing a logical left shift, and outputting the result to LEDs.

## Verification & Hardware Setup

### Simulation
Functional correctness was verified using **Xilinx Vivado Behavioral Simulation**. Using the `DIRISC_tb.vhd` testbench, the state of the Register File and ALU output were validated.

### FPGA Deployment
The design was synthesized and implemented on the **HAW MODSYS 2.0 board**. 
* **I/O Interfacing**: The I/O extension card was used to interface with physical switches and LEDs.
* **Execution**: The board was operated in **Single Clock Mode** for manual instruction stepping.

## Project Structure
* DIRISC_top.vhd: Top-level module
* DIRISC_control_unit.vhd: Instruction/Address decoding logic
* DIRISC_ALU.vhd: Arithmetic Logic Unit
* DIRISC_RF.vhd: Register File
* DIRISC_pmem.vhd: Program memory (Machine Code)
* DIRISC_global.vhd: Opcodes and constants

<img width="824" height="450" alt="WhatsApp Image 2026-05-07 at 22 58 11" src="https://github.com/user-attachments/assets/cca236df-bc3d-4d59-ad68-d5b9ec3701c1" />

<img width="1200" height="1600" alt="WhatsApp Image 2026-05-07 at 21 55 04" src="https://github.com/user-attachments/assets/38cdd507-326d-448f-b36f-7a00bcfc335a" />


