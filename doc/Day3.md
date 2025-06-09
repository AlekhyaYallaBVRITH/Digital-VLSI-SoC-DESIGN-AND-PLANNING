# 🧪 CMOS Fabrication Process: Inception of Layout

This document outlines the complete CMOS fabrication process, from substrate preparation to higher-level metal interconnect formation.

---

## 1️⃣ Create Active Regions

### Substrate Selection
We start with a p-type silicon substrate having high resistivity (5–50 ohm·cm), properly doped and oriented in the ⟨100⟩ direction.

### Active Region Formation
Regions where PMOS and NMOS will be formed are defined. Small isolated pockets are created for each transistor. Isolation between these pockets is ensured using LOCOS (Local Oxidation of Silicon).

1. Deposit SiO₂ layer (~40 nm)
2. Deposit Si₃N₄ layer (~80 nm)
3. Apply photoresist (~1 µm), pattern with Mask 1 using UV light
4. Etch the Si₃N₄ layer where exposed
5. Strip photoresist, oxidize exposed SiO₂ region
6. Remove Si₃N₄ using hot phosphoric acid

---

## 2️⃣ N-Well and P-Well Formation

P-well and N-well are formed using ion implantation:

- Use Mask 2 to protect regions and implant Boron (~200 keV) to form P-well.
- Use Mask 3 to implant Phosphorus to form N-well.
- Perform high-temperature annealing to activate the dopants and drive them deeper into the substrate.

---

## 3️⃣ Gate Terminal Formation

The gate terminal is the most critical for controlling threshold voltage.

1. Use Mask 4 to implant Boron in N-well
2. Use Mask 5 to implant Arsenic in P-well
3. Strip and regrow gate oxide using HF cleaning
4. Deposit doped polysilicon layer
5. Pattern the polysilicon using Mask 6 and etch

---

## 4️⃣ Lightly Doped Drain (LDD) Formation

LDD structures reduce hot carrier effects and short-channel issues.

- In P-well (NMOS), use Mask 7 to implant Phosphorus for N⁻ doping
- In N-well (PMOS), use Mask 8 to implant Boron for P⁻ doping
- Deposit oxide or nitride, then perform anisotropic etching to form spacers

---

## 5️⃣ Source and Drain Formation

To form source and drain regions:

1. Deposit thin screen oxide
2. In P-well, use Mask 9 to implant Arsenic (N⁺)
3. In N-well, use Mask 10 to implant Boron (P⁺)
4. Perform annealing at 1000°C to activate and form final source/drain

---

## 6️⃣ Local Interconnect Formation

1. Remove screen oxide
2. Sputter Titanium (Ti)
3. Heat wafer (~650–700°C in N₂) to form TiSi₂ and TiN
4. Use Mask 11 to etch TiN and define contact points
5. Remove unwanted TiN and photoresist

---

## 7️⃣ Higher-Level Metal Formation

1. Deposit thick SiO₂ with dopants
2. Planarize surface using CMP (Chemical Mechanical Polishing)
3. Use Mask 12 to etch via holes
4. Deposit TiN (~10 nm) as an adhesion/barrier layer
5. Fill vias with Tungsten (W) and CMP again
6. Deposit Aluminium (Al) for metal-1 layer
7. Use Mask 13 to etch Metal-1
8. Repeat process for Metal-2 with Mask 14 and 15
9. Final protection using SiO₂ or Si₃N₄ cap layer

---

## ✅ Final CMOS Output

After completing all fabrication steps, we have a functional CMOS chip with multiple interconnect layers and well-isolated PMOS/NMOS transistors.
![IMG-20250609-WA1666](https://github.com/user-attachments/assets/129dc772-4480-4a2d-ba37-207ffa692d82)
![IMG-20250609-WA1667](https://github.com/user-attachments/assets/521952e5-dcd2-42f0-bf0e-a7a95f00f316)
![IMG-20250609-WA1668](https://github.com/user-attachments/assets/0433a736-9948-40d9-a79c-4ec18d47e0f6)
![IMG-20250609-WA1669](https://github.com/user-attachments/assets/c8a125d0-cb0c-4de0-807b-35105091dff0)
![IMG-20250609-WA1670](https://github.com/user-attachments/assets/e4043dca-59fd-47bc-a3fe-cd0aa8b8acb4)
![IMG-20250609-WA1671](https://github.com/user-attachments/assets/82ad22ea-5dc9-4398-97be-e4fc190b54f1)
![IMG-20250609-WA1672](https://github.com/user-attachments/assets/1eba4728-d0c1-451e-a22a-4844a054e2bd)
![IMG-20250609-WA1673](https://github.com/user-attachments/assets/d3606160-459b-4cbc-a21b-cb3a9777335d)
![IMG-20250609-WA1674](https://github.com/user-attachments/assets/89726fea-48b5-43b9-9749-f1ffcd3029fc)
![IMG-20250609-WA1675](https://github.com/user-attachments/assets/7fc6b507-2082-4bbd-b04b-c59dd71284fb)
![IMG-20250609-WA1676](https://github.com/user-attachments/assets/b9a290b9-0ffd-4662-8630-7365e9d511ce)
![IMG-20250609-WA1677](https://github.com/user-attachments/assets/3ae8581a-d11c-42c2-920c-36c9b9174a51)
![IMG-20250609-WA1678](https://github.com/user-attachments/assets/9407abdd-c46a-4e87-95c0-8f4b693040e9)
![IMG-20250609-WA1708](https://github.com/user-attachments/assets/a3531af1-6a76-45df-96c8-27ead680c74e)
![IMG-20250609-WA1709](https://github.com/user-attachments/assets/0bf8a4a3-03fc-4ae2-a776-e2d92c55e8f3)

