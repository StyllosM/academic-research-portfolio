# MSc Thesis — Accelerating Deep Neural Networks with FPGAs

**University of Cyprus · MSc in Artificial Intelligence · 2025**  
**Academic supervisor:** Professor Theocharis Theocharides  
**Research context:** FPGA deployment and benchmarking of CNNs; related to broader work on adaptive/dynamic inference

## Research objective

My thesis investigated how convolutional neural networks (CNNs) could be mapped onto FPGA hardware, with an emphasis on a **repeatable ONNX-to-FPGA workflow**, practical board integration, resource feasibility and performance evaluation.

The broader research motivation concerned running different CNN configurations according to application needs. **The thesis itself implemented and evaluated static accelerators**; runtime switching, partial reconfiguration and a dynamic CNN scheduler were not implemented.

## Approach and my contributions

I first evaluated several practical deployment routes, including Vivado/Vitis HLS, Vitis AI and fpgaConvNet, encountering toolchain, compatibility and platform-support constraints.

The core work used **fpgaConvNet**, an existing research framework developed at Imperial College London. My contributions were to:

1. **Integrate and adapt official tutorials:** Consolidate their model preparation, ONNX export, parsing, partitioning, design-space exploration, optimization and HLS generation stages into the research notebook `8_All_In_One_ONNX`.
2. **Improve experimental repeatability:** Organize configuration and experiment outputs to make it easier to evaluate models and targets; retain logs and intermediate artifacts useful for diagnosis.
3. **Extend FPGA target descriptions:** Add platform/device specifications for further boards to support target-based feasibility studies.
4. **Broaden CNN coverage:** Investigate multiple ResNet, VGG-BN and MobileNetV2 variants, documenting successful mappings and parser/model compatibility limitations.
5. **Evaluate hardware and software agreement:** Use an ONNX Runtime CPU reference to compare the mapped FPGA outputs in the ZedBoard implementation documented in the thesis.

**Attribution:** I did **not** develop fpgaConvNet from scratch. The notebook is built upon the original framework and tutorials, including the [fpgaConvNet tutorial repository](https://github.com/AlexMontgomerie/fpgaconvnet-tutorial). Some experiments required local codebase modifications in addition to the notebook.

## Evaluation and results

### ZedBoard — Physical implementation and validation

The thesis documents Vivado integration, on-board execution, host–FPGA communication and comparison of FPGA outputs with the ONNX Runtime CPU reference. The best-performing reported configuration achieved approximately **224 μs compute-only latency**, corresponding to about **4,450 inferences/s at the accelerator level**.

**These are not complete application end-to-end timing measurements**: host preprocessing, UART transfers and other I/O overheads are not included in those kernel-performance numbers.

### KCU105 — Tool-based design-space exploration

The KCU105 was used as a **target configuration** for fpgaConvNet estimates across ResNet, VGG-BN and MobileNetV2 models. The analysis considered partitioning, LUT/FF/BRAM/DSP resource use, estimated latency and throughput. For example, **MobileNetV2 ×1.4 exceeded the modeled LUT budget (approximately 150% utilization)** in the reported configuration.

These are **analytical estimates, not measured KCU105 hardware results**. Being below a modeled resource budget does not itself establish successful physical implementation or timing closure.

## Notebook and reproducibility limitations

The uploaded `8_All_In_One_ONNX.ipynb` is a retained **experimental notebook with saved outputs and logs**. In particular, its saved MobileNetV2 ×0.5 / ZedBoard run includes resource-constraint warnings, testbench mismatches and incomplete processing. It should not be interpreted as a single clean, fully successful execution of every stage.

The **thesis**, rather than this notebook snapshot alone, is the supporting reference for the reported ZedBoard physical validation and the KCU105 comparison. A fresh execution may additionally require matching fpgaConvNet versions, modified parser/platform files, Vivado tools, hardware-specific integration and locally available dependencies not all included here.

## Files

- [MSc Thesis - Accelerating Deep Neural Networks with FPGAs.pdf](MSc%20Thesis%20-%20Accelerating%20Deep%20Neural%20Networks%20with%20FPGAs.pdf) — Full thesis, including methodology, board integration, measured ZedBoard results and estimated KCU105 comparisons.
- [MSc Thesis Presentation - Accelerating Deep Neural Networks with FPGAs.pptx](MSc%20Thesis%20Presentation%20-%20Accelerating%20Deep%20Neural%20Networks%20with%20FPGAs.pptx) — MSc thesis presentation.
- [MSc Thesis Code - 8_All_In_One_ONNX.ipynb](MSc%20Thesis%20Code%20-%208_All_In_One_ONNX.ipynb) — Integrated, tutorial-derived ONNX-to-fpgaConvNet notebook with saved execution logs.

## Main lesson

The thesis developed my experience with machine-learning inference, FPGA implementation and performance/resource evaluation. It also highlighted a recurring systems issue: **a fast accelerator kernel does not automatically imply a fast application when data movement, host processing and hardware interfaces are included**.

