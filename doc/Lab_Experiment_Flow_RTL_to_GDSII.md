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

: ~/Desktop/work/tools/openlane_working_dir/openlane/configuration contains the tool default configurations and README.md file inside that folder lists all the diffrent config variables avaible for the designer
priority : :~/Desktop/work/tools/openlane_working_dir/openlane/configuration < design/runs/config.tcl < design/PDK.tcl
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
# In a seperate terminal enter the directory with def filE (results folder in recent run stage : floorplan)
```tcl
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
