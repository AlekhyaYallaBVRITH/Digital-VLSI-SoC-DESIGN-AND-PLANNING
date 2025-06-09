

# 🧠 Digital VLSI SoC Design and Planning Workshop

A 5-day hands-on workshop focused on open-source EDA tools, layout design, cell characterization, and RTL2GDS implementation using SKY130 PDK.

---

## 📚 Table of Contents

- [Day 1: Introduction of Open Source EDA OpenLANE and SKY130 PDK](doc/Day1.md)  
- [Day 2: Good Floorplan vs Bad Floorplan and Introduction to Library Cells](#day-2-good-floorplan-vs-bad-floorplan-and-introduction-to-library-cells)(doc/Day2.md)
- [Day 3: Design Library Cell using MAGIC Layout & ngspice Characterization](#day-3-design-library-cell-using-magic-layout--ngspice-characterization)(doc/Day3.md)
- [Day 4: Pre-layout Timing Analysis and Importance of Good Clock Tree](#day-4-pre-layout-timing-analysis-and-importance-of-good-clock-tree)(doc/Day4.md)
- [Day 5: Final Step for RTL2GDS using TritinRoute and OpenSTA](#day-5-final-step-for-rtl2gds-using-tritinroute-and-opensta)(doc/Day5.md)
- [Lab_Experiments_Setup](doc/Lab_Experiment_Flow_RTL_to_GDSII.md)
---

## 🗓️ Day 1: Introduction of Open Source EDA OpenLANE and SKY130 PDK

- Overview of open-source VLSI workflows  
- Introduction to the SKY130 process design kit (PDK)  
- Setting up the environment and understanding the OpenLANE toolchain  
- Basic flow: synthesis, floorplanning, placement

---

## 🗓️ Day 2: Good Floorplan vs Bad Floorplan and Introduction to Library Cells

- What makes a floorplan “good” or “bad”  
- Floorplanning metrics and DRC violations  
- Understanding standard cells and custom cells  
- Anatomy of a library cell

---

## 🗓️ Day 3: Design Library Cell using MAGIC Layout & ngspice Characterization

- Using MAGIC layout tool to draw a NAND/NOR gate  
- LVS and DRC using Netgen  
- Extracting SPICE netlist  
- Characterization with ngspice for delay and power

---

## 🗓️ Day 4: Pre-layout Timing Analysis and Importance of Good Clock Tree

- Role of STA in VLSI flow  
- Pre-layout vs Post-layout timing  
- Basics of clock tree synthesis (CTS)  
- Importance of skew, latency, and buffering

---

## 🗓️ Day 5: Final Step for RTL2GDS using TritinRoute and OpenSTA

- TritinRoute for routing  
- Final DRC and LVS checks  
- Using OpenSTA for final timing analysis  
- Exporting GDSII and summary of end-to-end flow

---
## 🗓️ Steps to Conduct Lab Experiments RTL2GDS
## 🏁 Conclusion

This 5-day journey helped participants understand real-world digital VLSI backend workflows using fully open-source tools and SKY130 technology. Each module builds toward completing a digital RTL-to-GDSII flow.

---

## 👥 Contributors

- Alekhya [@your-github-handle]  
- [Add more team members if applicable]

---

## 📄 License

This project is licensed under the MIT License.




