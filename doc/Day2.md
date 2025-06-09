# 🗓️ Day 2: Good Floorplan vs Bad Floorplan & Introduction to Library Cells

---

## 🔧 Topics Covered
 It is the first step in physical design flow to find out the width and height. Let's begin with a netlist, netlist is two flipflops and have a simple combination logic in between. A netlist describes the connectivity of an electronic design. Here, we dependent on the dimensions of the logic gates(AND & OR) and particular flipflop. Now, let's convert the symbols into physical dimensions. We are interested in the dimensions of the Core and Die not in the dimensions of the wires.

Let's standard cell have dimensions of 1unit*1unit

So, area= 1 Sq. units

Asuume same area for the flipflop as well = 1 Sq. units

with help of dimensions and netlist let's calculate the area occupied by the netlist on a silicon wafer.

![318098509-abf79875-e1e3-4faf-87a6-43a12d44db8d](https://github.com/user-attachments/assets/248127dd-528e-4a7c-802c-a188fbe99b43)

## 📏 Utilization and Aspect Ratio in Floorplanning

### 🔹 Utilization

**Utilization** describes how much of the core area is occupied by logic cells such as standard cells, flip-flops, etc.

**Formula:**

`Utilization = (Area used by netlist) / (Total core area)`
---

### Aspect Ratio

Aspect Ratio defines the shape of the core area and impacts placement and routing efficiency.

`Aspect Ratio = Height of core / Width of core`
---
- **Ideal value:** ≈ 1.0 (square layout)
- A square shape offers balanced routing paths and fewer long nets.
- Non-square aspect ratios may be required for I/O or macro placement constraints.

---
🧱 Preplaced Cells : top level logic is broken into mutiple cuts and are implemented separately

Large reusable blocks (e.g., ALUs, comparators, muxes) can be implemented as preplaced IP blocks. *These cells are black-boxed and fixed in the layout before regular cell placement. *Decoupling Cells are placed around them to maintain stable voltage during power fluctuations by acting as capacitors.

decoupling cells help maintain stable supply voltage across the logic they are placed near , by provding capacitive charging effect in the event of supply voltage drop due to reistance on the pwr supply path

🔌 Power Planning:

A single power source leads to voltage drops in large circuits.

Power Meshes are used to distribute power efficiently across the chip.

📍 Pin Placement:

Pin positioning should reflect signal flow and reduce routing complexity.

A good understanding of internal logic is required for optimal pin placement.


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

