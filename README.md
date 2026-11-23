# Formula-EV-Hardware-Notes
> 🌐 **Language:** **🇺🇸 English (Main)** | [🇰🇷 한국어 (Korean)](README_KR.md)

## 📌 Project Overview
Circuit analysis, **LTspice simulations**, and **Altium Designer** PCB design notes for **Formula EV (KSAE/FSAE)** powertrain and safety systems.

The goal is to design reliable, noise-immune automotive electronics—including the **Vehicle Control Unit (VCU)**, **Shutdown Safety Circuits (BSPD, Pre-charge)**, and **HESS sensor interfaces**—while seamlessly integrating ECAD 3D models with **3DEXPERIENCE CATIA** mechanical enclosures.

---

## 🗺️ 4-Phase Hardware Development Roadmap

- [x] **Phase 0:** Repository setup & automotive PCB design rule check (DRC) standards
- [ ] **Phase 1: Circuit Simulation & Altium Fundamentals (`01_Circuit_Sim_Basics/`)**
  - LTspice switching/power simulations, custom schematic symbol/footprint library creation
- [ ] **Phase 2: FSAE/KSAE Safety Circuits (`02_Safety_Circuits/`)**
  - Analog Brake System Plausibility Device (BSPD), Pre-charge & Discharge circuit design
- [ ] **Phase 3: VCU & Sensor Interface PCB (`03_VCU_PCB_Design/`)**
  - MCU power supply (buck/LDO), CAN transceiver isolation, EMI/EMC grounding layout
- [ ] **Phase 4: ECAD-MCAD Co-Design (`04_ECAD_MCAD_Integration/`)**
  - 3D PCB clearance verification with aluminum waterproof enclosures in CATIA

---

## 📂 Design Log & Circuit Gallery

| No. | Folder / Circuit Name | Tools Used | Key Design Focus | Status |
| :--- | :--- | :--- | :--- | :--- |
| **01** | `01_MOSFET_LowSide_Driver` | LTspice | 3.3V/5V MCU to high-current load switching & gate ringing trade-off | 🔄 In Progress |
| **02** | `02_Power_Regulator_Test` | Altium Designer | 12V to 5V/3.3V Buck & LDO thermal PCB layout | ⏳ Planned |
| **03** | `03_BSPD_Safety_Board` | LTspice / Altium | Hardware comparator logic & fail-safe shutdown latch | ⏳ Planned |
| **04** | `04_VCU_Main_Controller` | Altium Designer | Dual-CAN bus, ADC sensor filtering, 4-layer PCB | ⏳ Planned |

---

## ⚡ Featured Circuit Study #01: MOSFET Low-Side Switching Driver Design

### 1. Objective
* Design and simulate a MOSFET switching circuit to safely drive high-current loads (e.g., cooling fans, shutdown relays) from a 3.3V/5V MCU signal.

### 2. Circuit Schematic & Simulation
* **Gate Resistor ($10\Omega$):** Limits inrush current to protect the MCU GPIO pin.
* **Pull-down Resistor ($10\text{k}\Omega$):** Prevents accidental turn-on when the MCU pin is floating.
* **Flyback Diode:** Protects the MOSFET from inductive voltage spikes.

### 3. Key Takeaways & Trade-offs
* Confirmed that lowering the gate resistor speeds up switching time and reduces heat loss, while a higher value reduces electromagnetic ringing.

---

## 🛠️ Hardware Documentation Standards
* **Simulation & Layout Evidence:** Every completed circuit includes **LTspice** waveform plots (`.png`), schematic captures, 2D/3D PCB layout renders, and a structured Bill of Materials (**BOM**).
* **Rule Compliance:** All high-voltage/low-voltage separation clearances strictly follow **KSAE / FSAE EV** technical regulations.
