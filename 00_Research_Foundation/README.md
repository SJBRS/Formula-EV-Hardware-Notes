# Hardware-Based Fault-Tolerant Bidirectional Sequential Control System with Schmitt Trigger Debouncing

## 1. Academic Research Background
* **Project Title:** Hardware-Based Fault-Tolerant Bidirectional Sequential Lighting Control System Utilizing Schmitt Trigger Debouncing Circuits
* **Engineering Problem:** Mechanical switch contact bouncing (chattering) and electrical noise often cause false triggering and sequential logic errors in multi-stage control systems. Relying solely on software delays introduces latency and vulnerability to electromagnetic interference (EMI).
* **Core Solution:** Designed a pure hardware-level signal conditioning circuit incorporating **RC low-pass filtering and Schmitt Trigger hysteresis** to eliminate contact bounce and ensure deterministic, fault-tolerant bidirectional switching without software overhead.

## 2. Iterative Hardware Design Workflow (V-Model Approach)
To verify signal integrity and prevent hardware faults prior to physical fabrication, a three-stage engineering workflow was executed:

* **Stage 1: Logic & Sequential Control Prototyping (`Tinkercad`)**
  * Validated bidirectional switching logic and state transitions across **4 controlled test cases (variable-controlled experiments)** to verify fault-free operation under different input sequences.
* **Stage 2: Analog Noise & Parametric Sweep Simulation (`LTspice`)**
  * Conducted **4 controlled parametric experiments** varying RC time constants and bounce durations alongside **Schmitt Trigger threshold voltages ($V_{T+}$ / $V_{T-}$)**.
  * Analyzed the trade-off between noise immunity (debounce filtering) and signal propagation delay to determine the optimal component values.
   ### 4-Case Controlled Variable Experiments (`LTspice` Ablation Study)
To independently verify the necessity of each hardware conditioning stage, a 4-case ablation study was simulated under identical switch bounce conditions (`PULSE` input, $V_{CC} = 5\text{V}$, $\tau = R_{\text{noise}} \cdot C = 100\text{k}\Omega \times 0.1\mu\text{F} = 10\text{ms}$):

| Test Case | Circuit Configuration | Removed Component | Engineering Purpose & Verification Outcome |
| :--- | :--- | :--- | :--- |
| **Case 1 (Top-Left)** | **Full System** (`RC Filter` + `74HC14` + `74HC86`) | **None (Baseline)** | **Fault-Free Operation:** RC filter suppresses high-frequency bounce while `74HC14` hysteresis restores sharp, glitch-free logic transitions. |
| **Case 2 (Top-Right)** | `74HC14` + `74HC86` | **Filter Capacitors (`0.1μF`)** | **Proves RC Filtering Necessity:** Without capacitive smoothing, fast bounce transients cross the Schmitt thresholds, causing false triggers. |
| **Case 3 (Bottom-Left)** | `RC Filter` + `XOR` | **Schmitt Trigger (`74HC14`)** | **Proves Hysteresis Necessity:** Slow RC charging edges linger near the standard logic threshold, inducing output oscillation and noise sensitivity. |
| **Case 4 (Bottom-Right)** | Bare `XOR` + Protection Resistors | **Both `RC Filter` & `74HC14`** | **Control Baseline:** Unconditioned switch bounce propagates directly to the output stage, resulting in severe sequential logic errors. |

* **Stage 3: Custom Library & Pre-Fabrication PCB Design (`Altium Designer`)**
  * Created custom schematic symbols and PCB footprints based on component datasheets.
  * Translated the verified LTspice analog circuits into a complete schematic and 2D/3D PCB layout, passing Electrical/Design Rule Checks (ERC/DRC) to ensure full manufacturing readiness.


## 3. Direct Application to Formula EV & Motorsport Engineering
* **Hardware Safety Interlocks (Shutdown Circuit):** In Formula EV and F1 vehicles, mechanical vibration and high-voltage inverter EMI can induce false signals on cockpit switches and safety interlocks. The exact **Schmitt Trigger debouncing and hardware-first reliability principles** proven in this research are directly applied to our Formula EV **Shutdown Circuit, Brake System Plausibility Device (BSPD), and VCU digital input conditioning**.

## 4. Extended Circuit Practice (`Encyclopedia of Electronic Circuits`)
Building upon the Schmitt Trigger research, additional reference circuits from Rudolf F. Graf's *Encyclopedia of Electronic Circuits* were analyzed and simulated to expand hardware design capabilities for Formula EV subsystems:

* **Component Selection & Analysis:** Selected and evaluated [74HC14 Schmitt Trigger Inverter / IRFZ44N Power MOSFET / LM393 Comparator] based on switching speed, threshold hysteresis, and voltage/current ratings.
* **Circuit Adaptation & Simulation (`LTspice`):** Adapted classic reference schematics into modern automotive low-voltage (12V/5V) environments and verified transient behavior, noise immunity, and power dissipation.
* **Key Learning:** Gained practical insight into reading datasheet parameters, sizing passive components (resistors/capacitors), and bridging textbook reference circuits to real-world PCB implementation.

