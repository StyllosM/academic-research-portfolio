# Academic Research Portfolio — Stylianos Mikeos

Research work completed during my BSc in Computer Engineering, MSc in Artificial Intelligence, and subsequent research appointments at the University of Cyprus. My interests include FPGA acceleration, hardware/software co-design, heterogeneous computing systems, quantum-computing simulation, and communications-oriented hardware.

This repository collects **research reports, thesis documents, presentations, and selected implementation notebooks**. It is intended to make the scope of each project, my individual contribution, and the available evidence easy to assess.

## Projects

| Project | Period | Scope and evidence |
| --- | --- | --- |
| [01-BSc-PSM-Lab](01-BSc-PSM-Lab/) | 2023–2024 | Four-person experimental BSc thesis on soil potential variations; theoretical and laboratory comparisons. Thesis and presentation **in Greek**, with an English README. |
| [02-MSc-FPGA-CNN-Acceleration](02-MSc-FPGA-CNN-Acceleration/) | 2025 | ONNX-to-FPGA workflow built around **fpgaConvNet**; physically validated ZedBoard implementation and separately reported KCU105 tool-based estimates. MSc thesis, presentation and selected notebook. |
| [03-IRIDA-Pasqal-Pulser](03-IRIDA-Pasqal-Pulser/) | 2026 | Python/Pulser **simulation-based** study of neutral-atom programming, graph optimization, noise sensitivity, and communications-inspired MIMO selection. Report and notebook. |
| [04-IRIDA-USRP-FPGA](04-IRIDA-USRP-FPGA/) | 2026 | FPGA/SDR **architecture and feasibility study** for an OFDM-PPPM receiver targeting NI USRP-2954R. No compiled FPGA implementation or hardware performance measurements. |

## How to interpret the results

The projects use different forms of evidence, which should not be conflated:

- **Physical hardware implementation and measurements:** Selected ZedBoard results in my MSc thesis; reported compute-only latency and throughput do not include the complete host–FPGA transfer path.
- **Analytical hardware estimates:** KCU105 CNN evaluations generated through fpgaConvNet; these were **not** validated by running the evaluated designs on a physical KCU105.
- **Quantum simulations:** Pasqal/Pulser experiments were run using simulation/virtual-device tools, **not a physical quantum processor**.
- **Design study only:** The USRP FPGA receiver was architected and specified but not synthesized, compiled, or tested on the physical device.
- **Collaborative laboratory results:** The BSc thesis was completed by four students and presents group experiments, not a solo research project.

Each project folder contains an English explanation of the task, my contribution, the results, limitations and links to the supporting material.

## Notes on reproducibility and attribution

The fpgaConvNet notebook adapts and integrates existing tutorials; **fpgaConvNet itself was developed by other researchers**. Some experiments depend on specific toolchain versions, platform-description changes, local development environments, or hardware not fully reproduced in this repository. The stored notebook outputs can include incomplete or unsuccessful runs. The project READMEs explain these boundaries.

The original BSc thesis and presentation are primarily in **Greek**. Their folder contains an English summary.

This repository is provided for academic review and reference. No blanket open-source license is asserted for third-party code or jointly authored documents; rights and permissions for the underlying materials remain with their respective holders.
