# Day 1: Introduction to Open Source EDA

## Topics Covered
- Introduction to OpenLANE
- SKY130 PDK
- Tool setup
## How to Talk to Computers?
Chips are packaged for easier mounting on embedded boards. Common packaging method: Wire Bonding.
The chip contains:
I/O Clearance Area: Hosts I/O pads
Core Area: Contains logic and memory
All within the Die Area
Foundries manufacture chips and may provide IP blocks (hard/soft macros).
ISA (Instruction Set Architecture): Assembly code just above machine language.
Typical software-to-hardware flow:
C code → Assembly → Machine code
RTL models hardware logic that runs the ISA-defined instructions.
System-on-Chip Design and OpenLANE Framework


## Essential Components
The open-source ASIC design implementation requires three fundamental elements:

RTL Designs
EDA Tools
PDK (Process Design Kit) Data
ASIC Implementation Flow
OpenLANE orchestrates the following sequential steps:

Synthesis: Converts RTL to PDK-specific physical library netlist  
Floorplan & Power Planning: Establishes die dimensions, pin configuration, and power distribution  
Placement: Positions standard cells within core region  
Clock Tree Synthesis (CTS): Implements clock distribution network  
Routing: Establishes signal interconnections  
Sign-off: Performs DRC, LVS, timing verification, and GDS generation

# 🚀 RISC-V Instruction Set Architecture

A beginner-friendly guide and hands-on resources for learning the **RISC-V ISA** — an open, free-to-use instruction set designed for modern processors.

---


## 🔍 Introduction

RISC-V is a **Reduced Instruction Set Computer (RISC)** architecture developed at UC Berkeley. It provides a modular ISA that can be used in everything from small embedded devices to powerful high-performance computing. RISC-V is a modern, open-standard Instruction Set Architecture (ISA) based on the principles of Reduced Instruction Set Computing (RISC). Developed at the University of California, Berkeley, RISC-V is designed to be simple, modular, and extensible, making it suitable for a wide range of computing applications—from embedded systems to high-performance processors. Unlike proprietary ISAs such as x86 or ARM, RISC-V is royalty-free and openly available, encouraging innovation and reducing barriers to entry for hardware design. Its base integer instruction set can be extended with standard modules for multiplication, atomic operations, floating-point arithmetic, vector processing, and compressed instructions. RISC-V supports 32-bit, 64-bit, and 128-bit data widths, offering excellent scalability. With growing support from industry and academia, and a vibrant ecosystem of tools, compilers, and operating systems, RISC-V is poised to become a dominant architecture in next-generation computing.

---

## Introduction to OpenLANE and ASIC Flow
OpenLANE is an automated RTL to GDSII flow designed for physical implementation of digital circuits using open-source tools and the Skywater 130nm PDK (SKY130). It integrates tools like Yosys, OpenROAD, Magic, Netgen, and others to streamline the full ASIC design flow, from synthesis to layout.
2. Toolchain Overview
The OpenLANE flow includes the following open-source tools:
- Yosys: for RTL synthesis
- OpenROAD: for floorplanning, placement, CTS, routing
- Magic: for layout generation and DRC
- Netgen: for LVS checks
- SPEF-Extractor, Klayout: for parasitic extraction and verification
3. Step-by-Step ASIC Flow with Diagrams
Synthesis
Converts RTL (Verilog) code to gate-level netlist using Yosys.

Floorplanning
Defines the core area, placement of macros, and I/O pin locations.  
Placement  
Places standard cells in the defined area while optimizing timing and area.  
Clock Tree Synthesis (CTS)  
Generates and balances the clock tree to minimize skew.  
Routing  
Connects all placed cells with metal layers considering DRC rules.  
GDSII Generation  
Creates the final layout in GDSII format for tapeout.  
DRC/LVS Checks  
Design Rule Check (DRC) and Layout vs Schematic (LVS) ensure layout correctness.  
4. Output Files  
Key output files generated in the OpenLANE flow include:
- synthesized.v (Netlist)
- def file (Design Exchange Format layout)
- .gds file (Final layout)
- .sdc file (Timing constraints)
- reports/ (Area, timing, power reports)



## Tools Used
- OpenLANE
- SKY130

