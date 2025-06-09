# 🕒 Delay Tables in Digital VLSI

Delay tables are fundamental in timing characterization of standard cells, enabling accurate modeling of delay and transition time for use in Static Timing Analysis (STA).

---

## 🔍 What Are Delay Tables?

Delay tables model how long a gate takes to respond to changing inputs and how fast its output transitions. These delays depend on:
- **Input transition (slew)**
- **Output load (capacitance)**

They are extracted during **standard cell characterization** and stored in **Liberty (.lib)** format.

---

## 🧠 Types of Delay Tables

| Table Type            | Description                                                  | Liberty Syntax        |
|-----------------------|--------------------------------------------------------------|------------------------|
| **Cell Delay Tables** | Propagation delay (input → output)                          | `cell_rise`, `cell_fall` |
| **Transition Tables** | Output slew based on input slew and load                    | `rise_transition`, `fall_transition` |

---

## 📦 Sample Liberty Format

```liberty
cell_rise (delay_template_1x1) {
    index_1 ("0.01");  // input transition (slew)
    index_2 ("0.01");  // output load (capacitance)
    values ("0.035");  // delay value in ns
}
rise_transition (delay_template_1x1) {
    index_1 ("0.01");
    index_2 ("0.01");
    values ("0.012");  // transition time in ns
}

---
# ⏰ Clock Tree Synthesis (CTS) and Signal Integrity

## Overview
Clock tree synthesis (CTS) is a critical step in the digital backend flow. It ensures the clock signal reaches all sequential elements (like flip-flops) with minimal skew and maximum signal integrity. TritonCTS (used in OpenROAD/OpenLANE flows) supports H-tree-based routing with buffers to balance delays and improve performance.

---

## 🧩 Naive Clock Routing and Skew

Initially, a simple clock net might connect directly to all flip-flops.

- Example: `clk1` connects to FF1 & FF2 of Stage 1, FF1 of Stage 3, and FF2 of Stage 4.
- Problem: Wire lengths vary → causes **clock skew**:  
  `Skew = t2 - t1 ≠ 0 ps`

This leads to race conditions, setup/hold violations, and unreliable timing.

---

## 🌳 Optimized Clock Tree (H-Tree Strategy)

To minimize skew:
- Clock root is placed at a **central location**
- Clock branches are **balanced symmetrically** (H-tree topology)
- Ensures clock signal reaches endpoints simultaneously

Same strategy applies to `clk2` and all branches.

---

## ⚙️ Clock Tree Buffering (Repeaters)

Due to RC effects in long clock routes:
- Signal degrades
- Input and output waveforms do not match

### Solution: Buffer Insertion
- Insert **clock buffers/repeaters** to restore signal strength
- Clock buffers are sized for **equal rise/fall times**
- Multiple repeaters may be inserted to maintain waveform fidelity

---

## ⚡ Signal Integrity: Crosstalk and Shielding

### Crosstalk Issue
- Adjacent nets (aggressors) can **induce noise** on the clock net (victim)
- Caused by **coupling capacitance**
- Results in **glitches**, **delta delay**, and increased **skew**

### 🔰 Shielding the Clock Net
- Place grounded/VDD wires between aggressor and victim
- These **non-switching wires** act as shields
- Reduce capacitive coupling and protect clock waveform

> ⚠️ Without shielding:
> - Noise impacts timing
> - Makes skew non-zero
> - Increases risk of functional failure

---

## ✅ Summary

| Technique         | Purpose                              |
|------------------|---------------------------------------|
| H-Tree Routing    | Minimize clock skew                  |
| Buffer Insertion  | Mitigate RC delay and waveform loss  |
| Shielding         | Protect against crosstalk interference|

---

## 🛠️ Tools Used

- **TritonCTS**: Open-source clock tree synthesis tool used in OpenROAD/OpenLANE flows
- **OpenROAD GUI**: Visualizes clock nets, skew, buffer placement, and shielding

