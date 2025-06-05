### 🧪 Laboratory Exercise Content Plan (Based on GitHub)

You can use this structure to create your lab exercises:

---

#### **Lab 1: RTL Design with TL-Verilog**

* **Objective:** Understand high-level hardware description with TL-Verilog.
* **Tools:** Makerchip IDE / command line
* **Tasks:**

  * Write a simple counter module.
  * Simulate using Makerchip or Verilator.
* **Expected Output:** Simulation waveform, functional RTL

---

#### **Lab 2: Simulation using Verilator**

* **Objective:** Perform simulation on TL-Verilog/Verilog designs
* **Tools:** Verilator
* **Tasks:**

  * Convert TL-Verilog to Verilog (if needed).
  * Compile and simulate using Verilator.
* **Expected Output:** Terminal waveform output / logs

---

#### **Lab 3: Synthesis with Yosys**

* **Objective:** Synthesize RTL into gate-level netlist
* **Tools:** Yosys
* **Tasks:**

  * Load RTL.
  * Perform synthesis using `synth -top <top_module>`.
  * Generate synthesized netlist.
* **Expected Output:** `.json` netlist file

---

#### **Lab 4: Floorplanning using OpenLANE**

* **Objective:** Create floorplan for design
* **Tools:** OpenLANE
* **Tasks:**

  * Configure floorplanning parameters (`DIE_AREA`, `CORE_AREA`, etc.).
  * Run `init_floorplan`.
* **Expected Output:** DEF file, floorplan layout images

---

#### **Lab 5: Placement, CTS & Routing**

* **Objective:** Carry out standard cell placement, clock tree synthesis, and routing
* **Tools:** OpenLANE
* **Tasks:**

  * Run `placement`, `cts`, `routing`.
* **Expected Output:** Updated DEFs, routed GDS view

---

#### **Lab 6: DRC & LVS with Magic and Netgen**

* **Objective:** Validate design using layout vs. schematic and design rule checks
* **Tools:** Magic, Netgen
* **Tasks:**

  * Open layout in Magic, run `drc`.
  * Compare layout vs netlist in Netgen.
* **Expected Output:** DRC clean confirmation, LVS match report

---

#### **Lab 7: GDSII Generation**

* **Objective:** Generate GDSII for fabrication
* **Tools:** OpenLANE / Magic
* **Tasks:**

  * Generate GDSII from final routed layout
* **Expected Output:** `.gds` file

---

#### **Lab 8: Power Analysis**

* **Objective:** Analyze power consumption
* **Tools:** OpenLANE or custom scripts
* **Tasks:**

  * Run power analysis on synthesized design
* **Expected Output:** Power report (leakage, dynamic)

---

#### **Lab 9: LEF/DEF File Creation**

* **Objective:** Create abstract layout files for integration
* **Tools:** OpenLANE
* **Tasks:**

  * Generate LEF/DEF from final layout
* **Expected Output:** `.lef`, `.def` files

---

#### **Lab 10: Post-layout Simulation**

* **Objective:** Simulate design after physical implementation
* **Tools:** Verilator + SDF or SPICE tools
* **Tasks:**

  * Extract netlist + delay.
  * Simulate using post-layout data.
* **Expected Output:** Functional waveform with delays

---

#### **Lab 11: Tape-out using SKY130**

* **Objective:** Prepare final files for tape-out
* **Tools:** OpenLANE, Magic
* **Tasks:**

  * Ensure DRC/LVS pass.
  * Package GDS, LEF, DEF, timing info.
* **Expected Output:** Complete GDS bundle for submission


### 📦 Prerequisites

Ensure the following tools are installed and properly configured:

- Docker
- Git
- Python 3
- OpenLANE (cloned and built)
- SKY130 PDK (via `open_pdks` or `make pdk`)
---
## 🛠️ Environment Setup for OpenLANE (`picorv32a` Design)

**Working Directory:**  
`~/Desktop/work/tools/openlane_working_dir/openlane`

**Design Directory:**  
`~/Desktop/work/tools/openlane_working_dir/openlane/design/picorv32a`

**Steps to Initialize OpenLANE:**
