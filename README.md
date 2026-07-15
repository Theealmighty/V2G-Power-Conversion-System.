# Bidirectional Vehicle-to-Grid (V2G) Power Conversion System

## Overview
This repository contains the simulation models and control architecture for a smart, bidirectional power interface between an Electric Vehicle (EV) battery ecosystem and a standard 3-phase AC distribution grid. The project utilizes **Model-Based Design (MBD)** methodologies to demonstrate intelligent load shifting and grid stabilization[cite: 4].

## Tech Stack & Tools
* **Modeling & Simulation:** MATLAB, Simulink, Simscape[cite: 4]
* **Control Logic:** Simulink Stateflow[cite: 4]
* **Verification & Deployment:** Simulink Test Manager, Model Advisor, Simulink Coder (Embedded Coder Target)[cite: 4]

## System Architecture
The top-level architecture is modularized into sequential conversion and control stages[cite: 4]:
1. **Physical Power Electronics Layer:** Features an active front-end DC-AC/AC-DC converter utilizing a 3-phase full-bridge IGBT configuration and an internal 5mH L-filter to ensure clean sinusoidal AC waveforms[cite: 4].
2. **DC-DC Conversion:** Integrates a buck-boost converter logic subsystem to strictly regulate the voltage for the EV battery and simulate parasitic auxiliary vehicle loads[cite: 4].
3. **EV Plant Model:** Parameterized battery model to capture transient dynamics, current/voltage sensing, and SOC depletion/replenishment curves[cite: 4].

## Finite State Machine Controller
The core intelligence of the system is the `V2G_Mode_Controller`, driven by a Stateflow finite state machine that transitions between three primary states[cite: 4]:
* **STANDBY (Mode 0):** Idle safety state triggered when SOC limits are reached (SOC >= 60 or SOC <= 20)[cite: 4].
* **G2V_CHARGING (Mode 1):** Active EV charging state triggered when overall grid demand is low[cite: 4].
* **V2G_DISCHARGING (Mode 2):** Energy injection mode triggered during peak stress to support the grid, extracting high-quality AC energy from the EV[cite: 4].

## Verification & Testing
* **Software-in-the-Loop (SIL):** The control logic was compiled into optimized C-code using Simulink Coder and verified against the behavioral model logic, achieving a 100% match[cite: 4].
* **Coverage:** Executed using the `ode23tb` stiff continuous solver to handle high-frequency switching, achieving 99% execution coverage during MIL testing[cite: 4].

## Getting Started
*(Provide instructions here on how to open the `.slx` files, which version of MATLAB is required, and how to run the simulation).*
