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

