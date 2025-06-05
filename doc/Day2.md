# 🗓️ Day 2: Good Floorplan vs Bad Floorplan & Introduction to Library Cells

---

## 🔧 Topics Covered

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

