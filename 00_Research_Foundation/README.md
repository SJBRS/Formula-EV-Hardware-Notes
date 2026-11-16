# Research & Hardware Design Workflow Foundation

## 1. Academic Research Background
* **Paper / Project Title:** [논문 또는 학부 연구 주제를 영문으로 적으세요]
* **Objective:** [연구를 통해 해결하고자 했던 핵심 공학 문제]
* **Key Findings:** [연구에서 도출된 핵심 수치나 시뮬레이션·실험 결과 요약]

## 2. Iterative Hardware Design Workflow (V-Model Approach)
To ensure reliability and minimize hardware prototyping errors before physical manufacturing, a three-stage verification workflow was established during undergraduate research:

* **Stage 1: Concept & Logic Prototyping (`Tinkercad`)**
  * Verified basic circuit topology, pin connections, and functional logic blocks at an early conceptual stage.
* **Stage 2: Analog Circuit & Transient Simulation (`LTspice`)**
  * Conducted detailed analog simulations to analyze voltage/current waveforms, switching losses, thermal limits, and noise filtering under dynamic load conditions.
* **Stage 3: Production Schematic & PCB Layout (`Altium Designer`)**
  * Translated verified simulation circuits into manufacturable schematics and multi-layer PCB layouts, applying proper trace width calculations, grounding, and high/low-voltage isolation rules.

## 3. Application to Formula EV Project
* This systematic workflow—combining academic modeling with **Tinkercad ➔ LTspice ➔ Altium Designer** verification—serves as the core engineering standard for developing the powertrain control and safety shutdown hardware of our Formula EV prototype.
