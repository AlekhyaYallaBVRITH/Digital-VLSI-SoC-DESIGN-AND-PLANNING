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
