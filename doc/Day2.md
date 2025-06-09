# 🗓️ Day 2: Good Floorplan vs Bad Floorplan & Introduction to Library Cells

---

## 🔧 Topics Covered
 It is the first step in physical design flow to find out the width and height. Let's begin with a netlist, netlist is two flipflops and have a simple combination logic in between. A netlist describes the connectivity of an electronic design. Here, we dependent on the dimensions of the logic gates(AND & OR) and particular flipflop. Now, let's convert the symbols into physical dimensions. We are interested in the dimensions of the Core and Die not in the dimensions of the wires.

Let's standard cell have dimensions of 1unit*1unit

So, area= 1 Sq. units

Asuume same area for the flipflop as well = 1 Sq. units

with help of dimensions and netlist let's calculate the area occupied by the netlist on a silicon wafer.

![318098509-abf79875-e1e3-4faf-87a6-43a12d44db8d](https://github.com/user-attachments/assets/248127dd-528e-4a7c-802c-a188fbe99b43)

`Utilization = (Area used by netlist) / (Total core area)`

- **Recommended range:** 50% to 80%
- **Too low:** Wastes silicon area, increases interconnect delay
- **Too high:** Leads to routing congestion, DRC violations, and timing failures

---

### 🔹 Aspect Ratio

Aspect Ratio defines the shape of the core area and impacts placement and routing efficiency.

\[
\text{Aspect Ratio} = \frac{\text{Height of core}}{\text{Width of core}}
\]

- **Ideal value:** ≈ 1.0 (square layout)
- A square shape offers balanced routing paths and fewer long nets.
- Non-square aspect ratios may be required for I/O or macro placement constraints.

---


### ✅ Good vs Bad Floorplanning
- Importance of floorplanning in chip design
- Basic objectives of a good floorplan:
  - Minimal congestion
  - Optimal area utilization
  - Power planning and placement
- Comparison of good vs poor floorplans using visualization

### ✅ Concepts Covered
- Core utilization
- Aspect ratio
- Pin placement
- Macro cell placement
- Routing blockage

---

## 🧱 Introduction to Library Cells

### What Are Standard Cells?
- Logic gates (NAND, NOR, INV)
- Flip-flops, latches
- DFF, buffers, etc.

### Library Cell Views:
- `.lef`, `.lib`, `.gds`, `.mag`, `.spice`
- Purpose of each view in the OpenLANE flow

### Practical Exploration
- Using OpenLANE’s `pdn.tcl` and `floorplan.tcl` scripts
- Viewing standard cells using Magic layout tool
- Parameters: Cell height, pitch, drive strength

---

## 🛠️ Tools Used

- OpenLANE
- Magic
- Netgen (for LVS checking)
- Library files from `sky130A` PDK

---

## 📸 Visual Examples

- [ ] Add screenshots of good vs bad floorplans
- [ ] Insert snapshots from Magic showing library cells

---

## 💡 Key Takeaways

- Floorplanning is a critical early stage that impacts timing, power, and routability.
- Standard cells are reusable blocks that form the basis of digital IC design.
- Open source tools like Magic and OpenLANE allow deep insight into standard cell design and integration.

---

