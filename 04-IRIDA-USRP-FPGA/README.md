# NI USRP-2954R — OFDM-PPPM Receiver FPGA Feasibility Study

**IRIDA Research Centre for Communication Technologies · University of Cyprus · 2026**  
**Research supervisor:** Professor Ioannis Krikidis  
**Work type:** FPGA/SDR **architecture and feasibility study**, not a completed implementation

## Objective

During my research assistantship at IRIDA, I suggested investigating whether repetitive operations from an existing **OFDM Power Peak Position Modulation (PPPM)** receiver could be moved from a **GNU Radio/Python host implementation** to the FPGA inside an **NI USRP-2954R** software-defined radio.

The proposed motivation was to perform sample-level processing close to the incoming data, potentially reducing host workload and intermediate data transfers while providing more deterministic execution. These were **anticipated benefits**, not experimentally measured improvements.

## My contribution

I investigated and documented a first-stage FPGA receiver architecture consisting of:

1. **Magnitude-squared calculation** for incoming complex I/Q samples.
2. **Slot-energy accumulation** over samples associated with each PPPM slot.
3. **Peak-slot selection** using a streaming maximum detector.
4. **PPPM symbol decoding and counters** for symbol and error statistics.

I also prepared fixed-point and data-width considerations, a proposed **host–FPGA register map**, and a staged block-level validation plan. The initial design assumed that payload samples were **already frame/slot aligned**; synchronization was outside the first version's scope.

The report specifies an illustrative first-version configuration with eight slots per PPPM symbol, 64 samples per slot and 1,000 payload symbols per experiment.

## Outcome and what was not implemented

The work ended at the **architecture, specification and feasibility** stage. A complete LabVIEW FPGA receiver, compilation/synthesis, bitstream generation, physical USRP execution and comparisons against the GNU Radio/Python baseline **were not completed**.

Progress was constrained by the required **NI/LabVIEW FPGA software environment and licensing**, which were unavailable under the group's existing arrangements. Given the project's priority and expected benefit, continuation was not cost-justified.

As a result, the report contains **no measured FPGA latency, throughput, CPU-load or bandwidth improvements**. The proposed design could serve as a starting point if a suitable toolchain becomes available or the architecture is migrated to another FPGA/SDR platform.

## File

- [IRIDA - FPGA_SDR - USRP2954R_PPPM_FPGA_Final_Report.pdf](IRIDA%20-%20FPGA_SDR%20-%20USRP2954R_PPPM_FPGA_Final_Report.pdf) — Receiver architecture, block specifications, host/FPGA register plan, design assumptions, licensing constraints, remaining work and project outcome.

## Main lesson

This feasibility study reinforced the importance of **hardware/software partitioning and data-movement costs**, as well as the impact of software ecosystems, licensing and implementation effort on whether an acceleration idea is practical.
