# Formula-EV-Hardware-Notes
Circuit analysis, LTspice simulations, and PCB design notes for Formula EV powertrain and safety systems.

# MOSFET Low-Side Switching Driver Design

## 1. Objective (학습 및 설계 목표)
* Design and simulate a MOSFET switching circuit to safely drive high-current loads (e.g., cooling fans, shutdown relays) from a 3.3V/5V MCU signal.

## 2. Circuit Schematic & Simulation (회로도 및 시뮬레이션)
* **Gate Resistor (10Ω):** Limits inrush current to protect the MCU GPIO pin.
* **Pull-down Resistor (10kΩ):** Prevents accidental turn-on when the MCU pin is floating.
* **Flyback Diode:** Protects the MOSFET from inductive voltage spikes.


## 3. Key Takeaways & Trade-offs (핵심 분석)
* Confirmed that lowering the gate resistor speeds up switching time and reduces heat loss, while a higher value reduces electromagnetic ringing.

