# Formula-EV-Hardware-Notes
Circuit analysis, LTspice simulations, and PCB design notes for Formula EV powertrain and safety systems.

# MOSFET Low-Side Switching Driver Design

## 1. Objective 
* Design and simulate a MOSFET switching circuit to safely drive high-current loads (e.g., cooling fans, shutdown relays) from a 3.3V/5V MCU signal.

## 2. Circuit Schematic & Simulation 
* **Gate Resistor (10Ω):** Limits inrush current to protect the MCU GPIO pin.
* **Pull-down Resistor (10kΩ):** Prevents accidental turn-on when the MCU pin is floating.
* **Flyback Diode:** Protects the MOSFET from inductive voltage spikes.


## 3. Key Takeaways & Trade-offs 
* Confirmed that lowering the gate resistor speeds up switching time and reduces heat loss, while a higher value reduces electromagnetic ringing.

