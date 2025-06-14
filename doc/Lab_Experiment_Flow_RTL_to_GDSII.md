### 🧪 Steps For Laboratory Exercise To Implement RTL to GDSII from DAY 1 TO Day 5


---

### Basic Linux Commands to start lab exercise

cd : opens the particular folder

ls : lists the content of the folder

pwd : shows the present working directory

mkdir : to make a new directory

command --help : shows the complete use that command   

clear : clears the terminal screen

---
### DAY 1 EXERCISE
## 🛠️ Environment Setup for OpenLANE (`picorv32a` Design)
## 🛠️ **Working Directory**

```bash
~/Desktop/work/tools/openlane_working_dir/openlane
```

---

## 📁 **Design Directory**

```bash
~/Desktop/work/tools/openlane_working_dir/openlane/design/picorv32a
```

## 🎯 **Target Design**

```text
picorv32a
```

---

## ⚙️ **Configuration Priority**

```text
Design-specific config.tcl overrides default tool parameters.
```

---

## 🧪 **Steps to Initialize OpenLANE**

### 🐳 Step 1: Start Docker Container

```bash
docker
```

### 🚀 Step 2: Launch OpenLANE Interface

```bash
./flow.tcl -interactive
```

### 📦 Step 3: Load OpenLANE Package (Inside OpenLANE Shell)

```tcl
package require openlane 0.9
```

### 🧬 Step 4: Prepare the Design

```tcl
prep -design picorv32a
```
![1](https://github.com/user-attachments/assets/fee1ba32-7096-4dfb-8246-b1eec197669d)
### Review files after design prep and run synthesis

After the preparation step, a run directory with the current date is created inside the picorv32a folder. It contains essential files for OpenLANE, including the merged.lef file in the temp folder, which holds key cell and routing layer information needed for layout and placement.
![2](https://github.com/user-attachments/assets/1e6d9afb-222b-4fd3-b962-1b02ba51781f)
![3](https://github.com/user-attachments/assets/18fecab1-b461-4aa7-badd-4262f1761f1d)

### 🧬 Step 5: Run Synthesis
```tcl
run_synthesis
# runs synthesis
```
After the run, the generated run directory contains key files: the results folder holds the synthesized netlist, reports includes synthesis reports (the latest one is most reliable), and logs stores all related log files.
![4](https://github.com/user-attachments/assets/7d1315e5-84a0-4149-a8e8-68f3fffa6741)
### 📊 DFF Ratio Calculation

At this step, we evaluate the **flip-flop (DFF) ratio** to understand sequential logic density in the design. The formula is:

```text
Flip Flop Ratio = (Number of D Flip Flops) / (Total Number of Cells)
Percentage of DFFs = Flip Flop Ratio × 100
```

📁 The synthesis report is located at:

```text
reports/synthesis/1-yosys_4.stat.rpt
```

From the report:

- Number of DFFs = `1613`
- Total number of cells = `14876`
So,

```text
Percentage of DFFs = (1613 / 14876) × 100 = 10.84%
```
---
### DAY2 EXERCISE
FLOORPLAN AND PLACEMENT  
```text
: ~/Desktop/work/tools/openlane_working_dir/openlane/configuration contains the tool default configurations and README.md file inside that folder lists all the diffrent config variables avaible for the designer
priority : :~/Desktop/work/tools/openlane_working_dir/openlane/configuration < design/runs/config.tcl < design/PDK.tcl
```
### 🧬 Step 5: Run FloorPlan
```tcl
run_floorplan
# runs floorplan
```
![5](https://github.com/user-attachments/assets/26cd8133-68bf-46c5-b50d-d95fd42a0cec)

## 📐 Die Area Estimation from Floorplan DEF

The **Floorplan DEF file** provides physical design dimensions in terms of **unit distances**. These unit distances are used to calculate the **actual die area** in microns.

---

### 🧮 Unit Conversion

- **1000 Unit Distance = 1 Micron**

---

### 📏 Floorplan Dimensions (in unit distance)

- **Width** = `660685 - 0 = 660685`
- **Height** = `671405 - 0 = 671405`

---

### 📦 Die Area Calculation

Area (in microns²) = (Width × Height) / (1000 × 1000)
                   = (660685 × 671405) / 1,000,000
                   = 443,587,208,925 / 1,000,000
                   = 443,587.21 µm²

---

### ✅ Result

- **Total Die Area** = `443,587.21 µm²`

---
**In a seperate terminal enter the directory with def filE (results folder in recent run stage : floorplan)**
```text
magic -T ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
## 🧭 Magic GUI: Navigating and Inspecting the Layout

### 🔹 Centering the Design
- Press **`s`** to select the entire design.
- Press **`v`** to center and zoom into the selected region.

---

### 🔍 Zooming into a Specific Area
- Move your cursor to the **bottom-left corner** of the area.
- **Left-click** to set the starting point `(x1, y1)`.
- Move your cursor to the **top-right corner** of the area.
- **Right-click** to complete the zoom box and focus in.

---

### 📌 Inspecting a Specific Object (e.g., Pin or Cell)
- Hover over the object you want to inspect (e.g., pin or cell).
- Press **`s`** to select the object.
- Open the **tkcon** (Magic's Tcl console).
- Type the command:

  ```tcl
  what
  
 ![9](https://github.com/user-attachments/assets/06c96a16-469e-4766-954b-e193e968e01b)
Floorplan data

![10](https://github.com/user-attachments/assets/9f34d414-1fbb-4e6f-829c-3a98cf0c870e)


### 🧬 Step 5: Run FloorPlan
The library holds cell data for timing and layout. In placement, netlist elements are arranged in the core area based on pin positions and interconnect estimates. Transition analysis checks delays; if needed, buffers are added to fix timing.
```tcl
run_placement
```
![11](https://github.com/user-attachments/assets/78b290f9-7ac4-4dd5-b45c-c9c1c8891c94)

To check def file generated in magic
**Open new terminal enter the directory with def file (results folder in recent run stage : placement)**
magic -T ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

To view the def file
![12](https://github.com/user-attachments/assets/c8f2a88c-b96e-47ee-a3e6-d039180e6d0d)
---

### Day 3 Exercise

### 🧬 Step 5: Design library cell using Magic Layout and ngspice characterization
Clone custom inverter standard cell design from github repository: nickson-jose vsdstdcelldesign.  
Load the custom inverter layout in magic and explore.

## Step 5.1 : Viewing Custom Inverter Layout in Magic

### 🛠️ Setup Instructions

1. **Enter OpenLane working directory**  
   *(Make sure you're inside the OpenLane environment)*

2. **Clone the custom inverter repo**:
   ```bash
   git clone https://github.com/nickson-jose/vsdstdcelldesign.git
   ```

3. **Enter the cloned repo**:
   ```bash
   cd vsdstdcelldesign
   ```

4. **Copy the Magic tech file to the working directory**:
   ```bash
   cp ../../pdks/sky130A/libs.tech/magic/sky130A.tech .
   ```

5. **Open the inverter layout in Magic**:
   ```bash
   magic -T sky130A.tech sky130_inv.mag &
   ```

---

### 🖱️ Magic GUI Controls

- Press **`s`** to select the element under the cursor.  
  Press **`s`** again to expand the selection to connected elements.

- In the **tkcon** console (inside Magic), type:
   ```tcl
   what
   ```
**Creating a folder in magic for git clone**
![15](https://github.com/user-attachments/assets/668a1696-6643-49f5-ae6f-18866c2158a0)
### GUI in magic for Standard cell

![16](https://github.com/user-attachments/assets/97c2d90c-fd37-41ff-b47a-75969845475a)
# PMOS
![17](https://github.com/user-attachments/assets/c6784e70-010f-462c-b260-ef879fadb673)

# NMOS
![18](https://github.com/user-attachments/assets/bcf16068-9106-4736-8cb5-12262ceda90b)

# Make drain connections of PMOS and NMOS
![19](https://github.com/user-attachments/assets/b2a02b78-df92-48e9-b0a0-3805dda29996) 
# Make GND to NMOS connection
![20](https://github.com/user-attachments/assets/94904a4e-a42e-4693-9833-8d2b3f26e13b)
#inside the magic tkconsole
extract all
# creates cell.ext file
ext2spice
# creates spice file
---
## Step 5.2 : Cell Characterization
After creating the cell layout, characterization is performed to evaluate parameters such as timing and noise. Timing characterization involves extracting parasitic elements—resistance (R) and capacitance (C)—from the layout. These parasitics are then used in circuit simulations to analyze the cell's dynamic behavior. For the inverter (INV) cell, transient analysis is typically conducted to determine key metrics including rise time, fall time, output transition time, and cell delay.
Here’s a rewritten and organized version of the steps to prepare the SPICE deck for simulation:

---

###  Steps to Prepare the SPICE Deck for Simulation

1. **Export Netlist from Magic:**

   * Use the `ext2spice` tool in Magic to extract the SPICE netlist from your layout.

2. **Edit the SPICE Netlist:**

   * Open the generated SPICE file in a text editor for modifications.

3. **Include Model Libraries:**

   * Add `.include` statements for the NMOS and PMOS model files (e.g., paths to `sky130_fd_pr__nfet_01v8` and `sky130_fd_pr__pfet_01v8`).

4. **Set Simulation Environment:**

   * Define simulation options such as grid size, temperature, and other global settings if required.

5. **Verify Device Models:**

   * Ensure the correct transistor models are used and their names match the included library files.

6. **Connect Power Rails:**

   * Add `.global` definitions for `VDD` and `GND`, and connect them appropriately in the circuit.

7. **Define Inputs and Outputs:**

   * Attach input signals (e.g., pulse source) and specify the output nodes where voltages will be observed.

8. **Set Simulation Type and Parameters:**

   * Specify the type of simulation (e.g., `.tran` for transient analysis) and define relevant parameters such as time step and total simulation time.

9. **End the Deck:**

   * Ensure the file ends with a `.end` statement to mark the conclusion of the SPICE deck.

---
# ngspice simulation commands
Command to directly load spice file for simulation to ngspice
```tcl
ngspice sky130_inv.spice
```
ngsice terminal will open, inside that make sure there is no errors, warnings mentioned. if errors are present, solve them first, before proceeding any further
```tcl
plot y vs time a
```
plotting output vs time and input

# Cell Characterization: Transition Times and Cell Delays

## Rise Transition Time Calculation

**Formula:**

```
Rise Transition Time = Time at 80% Vout − Time at 20% Vout
```

**Voltage levels:**

* 20% of Vout = **0.66 V**
* 80% of Vout = **2.64 V**

**Simulation Data:**

* Time at 80% Vout = **2.2468 ns**
* Time at 20% Vout = **2.1824 ns**

**Calculation:**

```
Rise Transition Time = 2.2468 ns − 2.1824 ns = 0.06396 ns = 64.0 ps
```

---

## 🔽 Fall Transition Time Calculation

**Formula:**

```
Fall Transition Time = Time at 20% Vout − Time at 80% Vout
```

**Voltage levels:**

* 20% of Vout = **0.66 V**
* 80% of Vout = **2.64 V**

**Simulation Data:**

* Time at 20% Vout = **4.0955 ns**
* Time at 80% Vout = **4.0530 ns**

**Calculation:**

```
Fall Transition Time = 4.0955 ns − 4.0530 ns = 0.0425 ns = 42.5 ps
```

---

## ⏱️ Rise Cell Delay Calculation

**Formula:**

```
Rise Cell Delay = Time (Output rises to 50%) − Time (Input falls to 50%)
```

**Reference Voltage:**

* 50% of VDD (3.3 V) = **1.65 V**

**Simulation Data:**

* Output at 50% = **2.21 ns**
* Input at 50% = **2.15 ns**

**Calculation:**

```
Rise Cell Delay = 2.21 ns − 2.15 ns = 0.06 ns = 60 ps
```

---

## ⏱️ Fall Cell Delay Calculation

**Formula:**

```
Fall Cell Delay = Time (Output falls to 50%) − Time (Input rises to 50%)
```

**Reference Voltage:**

* 50% of VDD (3.3 V) = **1.65 V**

**Simulation Data:**

* Output at 50% = **4.0780 ns**
* Input at 50% = **4.0501 ns**

**Calculation:**

```
Fall Cell Delay = 4.0780 ns − 4.0501 ns = 0.0279 ns = 27.9 ps
```

---
To download drc file into home directory folder
cd drc_tests                
**Navigate to the directory containing DRC test files**

vi .magicrc                
**Open the Magic configuration file in 'vi' editor**
```tcl
magic -d XR met3.mag &      
**Launch Magic in the 'XR' display mode and open the 'met3.mag' layout file**
```
---
Create a bounding box (bbox) in the layout window using the left and right mouse buttons.  
Select the desired layer by clicking it with the middle mouse button in the Layers panel.
![22](https://github.com/user-attachments/assets/718d01d2-37c5-429d-a07e-99e0cbd67d14)
![Screenshot from 2025-04-01 20-02-47](https://github.com/user-attachments/assets/2ca90b74-353f-4f1d-8231-586ab9879c21)

## Step 5.3 : Timing and Parasitic Extraction
These library files are typically generated using the Magic GUI, which extracts essential timing and parasitic information directly from the design layout.
**To rename the cell design**
save <new name>.mag

save sky130_vsdinv.mag

**open the design in new gui and write lef**
write lef <optional name, default is the design name in the gui> 
![Screenshot-37](https://github.com/user-attachments/assets/c2eeb345-4d2d-4874-90b0-1739525b90be)


* **Copy the `.lib` and `.lef` files** to the following directory:
  `design/<design_name>/src`
  *(Replace `<design_name>` with your actual design folder name.)*
![Screenshot-36](https://github.com/user-attachments/assets/5d27f987-b21c-470b-b0bf-95f6dda4e810)

Edit the design/config.tcl file to include the paths to the newly added .lib and .lef files in the src folder. This ensures that the OpenLANE flow uses the updated library and layout information during the design process.

**Set paths to different timing corner library files**
set ::env(LIB_SYNTH)   "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

**Include any additional LEF files from the src directory**
set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]  

These settings ensure the OpenLANE flow uses your updated .lib and .lef files for synthesis, placement, and routing.

**Open the openlane terminal**
cd Desktop/work/tools/openlane_working_dir/openlane

docker

./flow.tcl -interactive

**Inside openlane terminal**

**below cmd to be used to overwrite previous run data** 
```tcl
prep -design picorv32a -tag <prev run folder inside /runs> -overwrite 
```
**Cmds to include the new cell led in merged.lef in /tm[ folder**
```tcl
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```
```tcl
run_synthesis
```
After completing the synthesis run, review the generated reports to analyze key performance metrics. Focus on the chip area to understand the total physical space occupied by the design. Additionally, examine the timing results, particularly the Worst Negative Slack (WNS) and Total Negative Slack (TNS), which indicate how well the design meets its timing constraints. These values help assess whether the synthesized circuit operates within the desired clock period and identify potential timing violations that need to be addressed in later stages.
The presence of the custom sky130_vsdinv cell in temp/merged.lef indicates that the cell was successfully included and utilized during the synthesis process. This confirms that the OpenLANE flow correctly recognized and integrated the custom cell into the design.
![Screenshot from 2025-04-02 20-15-58](https://github.com/user-attachments/assets/5cebbbb6-a41b-4673-a8b9-96949bfde7b7)

To improve the timing of the design during synthesis, we can alter some of the variables (like SYNTH_SIZING, SYNTH_STRATEGY, SYNTH_BUFFERING from configurations/README.md) to get desired results Variable information in configurations/README.md

Changing the variables in openlane terminal

Command to display current value of variable SYNTH_STRATEGY

```tcl echo $::env(SYNTH_STRATEGY)
```

**Command to set new value for SYNTH_STRATEGY**

```tcl
set ::env(SYNTH_STRATEGY) "DELAY 3"
```
**Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled , if enabled =1**
```tcl
echo $::env(SYNTH_BUFFERING)
```
**Command to display current value of variable SYNTH_SIZING, if enabled =1**
```tcl
echo $::env(SYNTH_SIZING)
```
**Command to set new value for SYNTH_SIZING**
```tcl
set ::env(SYNTH_SIZING) 1
```
**Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not**
```tcl
echo $::env(SYNTH_DRIVING_CELL)
```
```tcl
run_synthesis
```
# To check the synthesized netlist 
Open the netlist file generated after synthesis sky130_vsdinv in temp/merged.lef

![Screenshot from 2025-04-02 20-15-58](https://github.com/user-attachments/assets/9a80bbfa-805d-40d4-8eff-50637547a116)
To improve timing, adjust variables like SYNTH_SIZING (enables gate resizing), SYNTH_STRATEGY (sets optimization level), and SYNTH_BUFFERING (inserts buffers). Tweaking these helps meet timing goals.
**Command to display current value of variable SYNTH_STRATEGY**
echo $::env(SYNTH_STRATEGY)

**Command to set new value for SYNTH_STRATEGY**
set ::env(SYNTH_STRATEGY) "DELAY 3"

**Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled , if enabled =1**
echo $::env(SYNTH_BUFFERING)

**Command to display current value of variable SYNTH_SIZING, if enabled =1**
echo $::env(SYNTH_SIZING)

**Command to set new value for SYNTH_SIZING**
set ::env(SYNTH_SIZING) 1

**Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not**
```tcl
echo $::env(SYNTH_DRIVING_CELL)
Next if we do run_synthesis to update all the changes made.
next followed by run_floorplan
```
---
## Step 6 : Timing Analysis with Ideal Clocks Using OpenSTA
create pre_sta.conf to define the files to be loaded to the opensta for analysis in diffrent corners
![Screenshot-27](https://github.com/user-attachments/assets/63f92396-7038-413f-b2ea-6f3855ecff15)
create mybase.sdc file to define timimng contraints info for the sta tool. place it in designs/picorv32a/src and now run the opensta tool
```tcl
sta pre_sta.conf
```
** For Optimization**
Reopen the openlane to implememt any changes

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a -tag 03-04_09-49 -overwrite

# Adiitional commands to include custom lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

**Command to set new value for SYNTH_STRATEGY**
set ::env(SYNTH_STRATEGY) "DELAY 3" 

**Command to set new value for SYNTH_SIZING**
set ::env(SYNTH_SIZING) 1

**Command to set new value for SYNTH_MAX_FANOUT**
set ::env(SYNTH_MAX_FANOUT) 4

#Now that the design is prepared and ready, we can run synthesis using following command
run_synthesis

** open new sta cmdline in new terminal**
```tcl
sta pre_sta.conf
```
**Eco implementation**
Identify problematic cells from the design The oai cell seems to be driving 4 cells.
![30139ce0-b8bc-48f9-aeb6-4f7c49e92cf1](https://github.com/user-attachments/assets/c0976f61-bd33-444d-9e8f-a69e6ad52601)
**Report all connections to a specific net**
report_net -connections _04373_

**Check syntax for a command**
help replace_cell

**Replace a cell in the design**
replace_cell _22324_ sky130_fd_sc_hd__o21ai_4

**Generate a custom timing report with specific fields**
report_checks -fields {net cap slew input_pins} -digits 4
The slack improved from -4.62 to -4.58

Nand gate of strength 2 is driving three cells
-changing drive stength to 3 returns the message "Warning: liberty cell 'sky130_fd_sc_hd__nand2_3' not found."
-changing the drive strength to 4  the slack reduced to -4.5555 from -4.5886
![Screenshot-21](https://github.com/user-attachments/assets/86af29bb-38a7-4896-abd8-6aa445e3b51c)
The OAI cell with drive strength 2 shows higher delay. When you try changing the drive strength to 3, you get this warning:
`Warning: liberty cell 'sky130_fd_sc_hd__o21bai_3' not found.`

Changing the drive strength to 4 works without errors.
![Screenshot-22](https://github.com/user-attachments/assets/0e91e8af-baca-4093-abb6-a84757aa9c77)
The slack will be reduced from -4.5555 to -4.5060
To check the timing through the modified cell.
```tcl
report_checks -from _35312_ -to _35239_ -through _22380_
```
**report_checks -from _start_pont_net_id -to end_point_net_id -through cell_id**
## Step 7 : Timing analysis with real clocks using openSTA
OpenROAD is the core tool on which OpenLane is built. It includes a built-in STA engine that we will use to analyze timing.
docker

./flow.tcl -interactive

package require openlane 0.9

#to start with previous data without overwrite tag
prep -design picorv32a -tag 03-04_09-49 
# INit Openroad terminal inside openlane terminal
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/03-04_09-49 /tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/03-04_09-49/results/cts/picorv32a.cts.def

**Creating an OpenROAD database to work with**
write_db pico_cts.db

**Loading the created database in OpenROAD**
read_db pico_cts.db

**Read netlist post CTS**
read_verilog /openLANE_flow/designs/picorv32a/runs/03-04_09-49/results/synthesis/picorv32a.synthesis_cts.v

**Read library for design**
read_liberty $::env(LIB_SYNTH_COMPLETE)

**Read in the custom sdc we created**
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

**Setting all cloks as propagated clocks**
set_propagated_clock [all_clocks]

**Generating custom timing report**
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

**Exit to OpenLANE flow into openRoad**
exit
![Screenshot-19](https://github.com/user-attachments/assets/f38fd07a-9459-4e25-8edb-5f166489ccf6)
Hold slack
![Screenshot-18](https://github.com/user-attachments/assets/b39e0851-4c3b-4caf-8b9b-0a1bf50ac40c)
Setup slack
![Screenshot-17](https://github.com/user-attachments/assets/d4679add-8dc0-40e2-abd7-f59e23c794fb)
After this,
removing "sky130_fd_sc_hd__clkbuf_1'" from CTS_CLK_BUFFER_LIST and reruning the cts to see the results
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Setting def as placement def otherwise, we get clock not found error
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/04-04_09-02//results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/04-04_09-02//tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/04-04_09-02//results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/04-04_09-02//results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit


# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

Before removal of "sky130_fd_sc_hd__clkbuf_1" values are
| Slack Type | Value (ns) | Status  |
|------------|------------|---------|
| Hold       | 0.0637     | MET     |
| Setup      | 4.5985     | MET     |

After removing "sky130_fd_sc_hd__clkbuf_1" values are
| Slack Type | Value (ns) | Status  |
|------------|------------|---------|
| Hold       | 0.2351     | MET     |
| Setup      | 4.6943     | MET     |
### 🧬 Step 6: PWR Routing
#step 6.1: Generation of pdn.def file

**check which def file openlane is currently pointing at , it should be pointing to CTS def**
echo $::env(CURRENT_DEF)

**create PDN**
gen_pdn
![Screenshot-15](https://github.com/user-attachments/assets/f9514eca-2d4c-489f-a3ca-07b9bd9197fb)
 To view the pdn file
 
```tcl
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/04-04_09-02/tmp/floorplan

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../merged.lef def read 12-pdn.def &
```
#step 6.2: Routing 
```tcl
run_routing
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/04-04_09-02/results/routing/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
# step 6.3: To verify the results open the OpenRoad tool
openroad
```tcl
# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/04-04_09-02/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/04-04_09-02/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/04-04_09-02/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/04-04_09-02/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```
Hold and Setup
![day 5-2 (1)](https://github.com/user-attachments/assets/f3c7b440-0fb3-432e-ae5a-33314f7daf1e)

![day 5-1 (1)](https://github.com/user-attachments/assets/d872ce77-c16f-4492-a579-5b1087f868b2)
## Final Slack Values

| Slack Type | Value (ns) | Status  |
|------------|------------|---------|
| Hold       | 0.1079     | MET     |
| Setup      | 4.3674     | MET     |

