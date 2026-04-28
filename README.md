# Phoenix: FPGA-Based Intelligent Traffic Light Controller 🚦

An adaptive, FPGA-based traffic management system designed to prioritize emergency vehicles, ensure pedestrian safety, and detect sensor faults in real-time. 

[cite_start]Developed by **Team Phoenix** for the VLSI domain of the SYMBIOT Hackathon (April 24-25, 2026) at Vidyavardhaka College of Engineering[cite: 1, 4, 8, 11, 13].

## ⚠️ The Problem
[cite_start]Traditional, fixed-time traffic signals fail to adapt to real-world, dynamic conditions[cite: 19]. This leads to critical issues:
* [cite_start]**Emergency Delays:** Ambulances get stuck at red lights, increasing response times[cite: 20].
* [cite_start]**Pedestrian Risks:** Crosswalk requests are not handled efficiently or safely[cite: 22].
* [cite_start]**Unreliability:** Existing models rarely detect hardware or sensor faults, causing false decisions[cite: 23, 26].

## 💡 Our Solution
[cite_start]We developed an intelligent traffic controller that reacts to live conditions[cite: 76]. [cite_start]By utilizing an FPGA, the system achieves fast, low-latency, and deterministic hardware-level parallel processing[cite: 51, 79].

### Key Features
* [cite_start]**Emergency Vehicle Priority:** Instantly overrides normal flow to clear paths for ambulances using IR/RFID detection[cite: 45, 105, 158].
* [cite_start]**Pedestrian Support:** Dedicated request inputs and WALK signals with audible buzzers ensure safe crossings[cite: 61, 67, 106].
* [cite_start]**Adaptive Density Control:** Adjusts green-light durations based on live traffic density (Low, Medium, High)[cite: 104, 132].
* [cite_start]**Sensor Health Checks:** Uses redundant sensors to detect and alert maintenance of hardware faults via XOR mismatch logic[cite: 23, 59, 120].

## 🛠️ Tech Stack & Hardware
* [cite_start]**Hardware Platform:** ARTY A7-100T FPGA Board[cite: 49].
* [cite_start]**Language:** Verilog HDL[cite: 48].
* [cite_start]**Development Tool:** AMD Vivado 2025.2[cite: 103].
* [cite_start]**Control Methodology:** Finite State Machine (FSM)[cite: 49].

## 🧠 System Architecture
[cite_start]The core logic is driven by a Priority Arbiter and a Countdown Timer integrated into an FSM[cite: 45, 46]. 

**State Flow & Priorities:**
[cite_start]`EMERGENCY > SENSOR FAULT > PEDESTRIAN > ADAPTIVE NORMAL FLOW` [cite: 131]

*(Optional: Add a screenshot of your block diagram from the presentation here)*
`![System Architecture](./docs/architecture.png)`

## 🚀 Getting Started

### Prerequisites
* [cite_start]AMD Vivado 2025.2 or later[cite: 103].
* [cite_start]ARTY A7-100T development board[cite: 103].

### Simulation
1. Clone this repository: `git clone https://github.com/HarshKarnaa818981/phoenix.git`
2. [cite_start]Add `src/traffic_controller.v` to your Vivado simulation sources.
3. [cite_start]Run the behavioral simulation to verify FSM state transitions based on the `TIMER_BITS = 8` simulation parameters[cite: 103].

### Hardware Implementation
1. [cite_start]Modify the timer parameters in `traffic_controller.v` to match the 100 MHz hardware clock (e.g., `30 * 100_000_000`)[cite: 103, 105].
2. Synthesize and implement the RTL design[cite: 72].
3. Generate the bitstream and program the ARTY A7-100T board[cite: 72].
