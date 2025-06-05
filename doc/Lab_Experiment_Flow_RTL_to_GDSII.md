### 🧪 Steps For Laboratory Exercise To Implement RTL to GDSII

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
```bash
~/Desktop/work/tools/openlane_working_dir/openlane
---
**Design Directory:**
```bash 
`~/Desktop/work/tools/openlane_working_dir/openlane/design/picorv32a`
---
Target Design: picorv32a
---
Configuration Priority: Design-specific config.tcl overrides default tool parameters
---
**Steps to Initialize OpenLANE:**
```bash
docker                    # Initialize Docker container
./flows.tcl -interactive  # Launch OpenLANE interface
package require openlane 0.9  # Load OpenLANE 0.9
prep -design picorv32a    # Initialize picorv32a design
