# Pasqal/Pulser — Neutral-Atom Quantum Simulation and Optimization

**IRIDA Research Centre for Communication Technologies · University of Cyprus · 2026**  
**Research supervisor:** Professor Ioannis Krikidis  
**Work type:** Python-based, **simulation-only** practical evaluation

## Objective

I investigated Pasqal's neutral-atom quantum-computing platform using **Pulser**, its Python framework for defining atom registers and pulse-level control sequences. The goal was to build a practical reference that the research group could use when evaluating the platform for possible future simulation or quantum-computing research.

The study progressed from foundational physical behaviours to small graph-optimization and communications-inspired examples, with classical baselines and explicit discussion of the simulator's limits.

## My work

- **Platform programming:** Atom geometry, pulse sequences, Rabi oscillations, Rydberg blockade, simple chains and square registers.
- **Reusable graph-to-Pulser workflow:** Map graph instances to atom coordinates, simulate measurement distributions, score valid independent sets and compare results with **exact classical solutions**.
- **Pulse sensitivity and robustness:** Parameter scans; controlled dephasing and state-preparation-and-measurement (SPAM) noise studies.
- **Graph-size transfer:** Evaluate a fixed pulse schedule across small path graphs (four through eight nodes).
- **Weighted optimization:** A small maximum-weight independent-set (MWIS) study using a **Detuning Map Modulator (DMM)** for local weighting.
- **Wireless communication example:** MIMO configuration selection with a QUBO-style formulation, simulated annealing, classical exhaustive search and direct SNR/Shannon-capacity objectives.

## Selected simulation results

- For a **four-node square MIS** problem, the best tested pulse-setting run produced a reported **0.991** probability of sampling an optimal independent set (1,000 samples).
- A fixed-schedule path-graph study found that optimal-solution sampling probabilities varied across problem sizes, despite consistently high valid-independent-set probabilities.
- In a **four-node weighted square** example, the classically verified weighted-optimal bitstring `1001` appeared in **1,000/1,000 samples** with DMM weighting, compared with **477/1,000** in the unweighted reference. This was an **idealized MockDevice simulation**, not a real-hardware result.
- The MIMO investigation tested small configuration-selection problems against exact classical search. The **Pulser-based MIMO prototype enforced candidate feasibility through geometry**; the complete weighted communication objective was **evaluated classically after sampling**, not directly encoded in the neutral-atom Hamiltonian.

## Scope and limitations

**No physical Pasqal QPU was used.** All quantum results are based on local simulation or virtual-device models. Reported probabilities depend on pulse choices, geometry, sampling and simulation assumptions. Noise parameters were controlled sensitivity variables, not hardware-calibrated measurements. No quantum advantage, QPU runtime advantage or general-purpose large-scale optimization result is claimed.

The project provides a reusable learning and experimental foundation for later **device-constrained emulation, calibrated noise modelling and hardware studies**, should access become available.

## Files

- [IRIDA - Pasqal - Pulser Simulation Extended Report.pdf](IRIDA%20-%20Pasqal%20-%20Pulser%20Simulation%20Extended%20Report.pdf) — Technical report with methodology, experiment results, classical validation, noise/graph-scaling studies and limitations.
- [IRIDA - Pasqal - Pulser Simulation Extended Code.ipynb](IRIDA%20-%20Pasqal%20-%20Pulser%20Simulation%20Extended%20Code.ipynb) — Python/Pulser notebook with simulation code and saved experimental outputs.

## Reproducibility note

The notebook depends on Python scientific-computing and Pulser simulation libraries. Some examples use virtual or mock devices; the same pulse parameters are **not necessarily executable on a particular physical Pasqal processor**. Consult the report for the exact meaning of each result and the code for its associated simulation settings.

