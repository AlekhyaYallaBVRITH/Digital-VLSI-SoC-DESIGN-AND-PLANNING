### 🧪 Steps For Laboratory Exercise To Implement RTL to GDSII

### 📦 Prerequisites

Ensure the following tools are installed and properly configured:

- Docker
- Git
- Python 3
- OpenLANE (cloned and built)
- SKY130 PDK (via `open_pdks` or `make pdk`)
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

---

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

