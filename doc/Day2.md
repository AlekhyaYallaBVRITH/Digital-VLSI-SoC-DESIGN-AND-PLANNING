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
Example:
![WhatsApp Image 2025-06-09 at 10 19 25_47a44d4d](https://github.com/user-attachments/assets/7fee9a7e-61c9-4b1e-a7af-2eee18ee2d62)
![WhatsApp Image 2025-06-09 at 10 19 44_86d5d46a](https://github.com/user-attachments/assets/c19f5875-94a9-496b-bc25-1f37ad80a330)

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

### Need for libraries and characterization
Every ICdesign Flow needs to go through the several steps. First step to go through is Logic Synthesis, let's say if we have a functionality which is coded in a form of an RTL so first we need to convert the functionality into legal hardware is refered to as Logic Synthesis. Ouput of the logic synthesis is arrangement of gates that will represent the original functionality that has been described using an RTL. Next step of logic synthesis is Floorplaning, in this we omport the output of logic synthesis and decide the size of the Core and Die. The next step after floorplaning is Placement, in this we take the particular logic cell send place them on the chip in such a fashion that initial timing is better. Next step is CTS(Clock tree synthesis), in this we take care that clk should reach each and every signal at the same time also take care of each clk signal has equal rise and fall.Next step is Routing, routing has to go through the certain flow dependendent on the characterization of the flip flop.And now comes the last step STA(Static timing analysis), in this we try to see the set up time, hold time, maximum achieved frequency of the circuit. One common thing across all stages 'GATES or Cells'.

## 🛠️ Tools Used

- OpenLANE
- Magic
- Netgen (for LVS checking)
- Library files from `sky130A` PDK

---


