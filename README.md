# 45nm-PLL-Design
Cadence Virtuoso design and simulation of a charge-pump PLL in 45nm CMOS.

### 1. AI-Driven LO Synthesizer on 45nm CMOS PLL
*Tech Stack: Cadence Virtuoso, Spectre, Python, PyTorch, Reinforcement Learning*

*   **The Hardware Baseline:** Engineered a complete charge-pump Phase-Locked Loop (CPPLL) at the transistor and gate level using a 45 nm CMOS process. The initial baseline achieved stable lock and drift-free control voltage.
*   **AI Pre-Charge Neural Network:** Designed a feedforward Artificial Neural Network (ANN) in PyTorch to predict steady-state control voltage (Vc) and pre-charge the loop filter. This AI intervention targets a massive lock acquisition time reduction from ~5.0 µs down to < 250 ns.
*   **Reinforcement Learning & Calibration:** Developed an RL-based adaptive tuner to dynamically adjust loop filter and charge-pump trim, trading speed for jitter as needed. Implemented a background digital calibration loop to cancel charge-pump mismatch, targeting a reference spur floor below -58 dBc.
*   **Co-Simulation Infrastructure:** Built a custom bridging environment between Cadence Spectre and Python using an OCEAN script and shared-memory IPC, allowing the PyTorch models to actively control the Spectre transient simulation.

### AI Optimization & Co-Simulation Workflow
The flowchart below details the Multi-Objective Particle Swarm Optimization (MOPSO) pipeline developed to automate design space exploration. Python generates parameterized netlists, Cadence Spectre executes the transistor-level simulations, and the algorithm optimizes for lock time, phase noise, and power.

![MOPSO Co-Simulation Workflow](MOPSO_Optimization_Flowchart.jpg.jpg)

*Note: Full block-level schematics (PFD, Charge Pump, Current-Starved VCO, Divider) and Spectre transient response plots are available in the repository files above.*
