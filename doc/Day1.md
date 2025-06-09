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

## Tools Used
- OpenLANE
- SKY130

