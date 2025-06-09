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

## 📚 Table of Contents

- [Introduction](#introduction)
- [Why RISC-V?](#why-risc-v)
- [RISC-V Base and Extensions](#risc-v-base-and-extensions)
- [Instruction Formats](#instruction-formats)
- [Example Programs](#example-programs)
- [Tools and Simulators](#tools-and-simulators)
- [References](#references)

---

## 🔍 Introduction

RISC-V is a **Reduced Instruction Set Computer (RISC)** architecture developed at UC Berkeley. It provides a modular ISA that can be used in everything from small embedded devices to powerful high-performance computing.

---

## ❓ Why RISC-V?

- ✅ Open-source and royalty-free
- ✅ Modular and extensible
- ✅ Easy to implement and understand
- ✅ Supported by compile



## Tools Used
- OpenLANE
- SKY130

