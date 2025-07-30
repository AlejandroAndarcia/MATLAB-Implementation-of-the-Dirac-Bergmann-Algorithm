# MATLAB-Implementation-of-the-Dirac-Bergmann-Algorithm

**Brief description.**  
This MATLAB code automates the Dirac–Bergmann constraint formalism to analyze **singular** Lagrangian systems.

> **Acknowledgment.** Parts of this codebase and documentation were developed **with the assistance of ChatGPT**.

---

## Features

- Full Dirac–Bergmann workflow for symbolic Lagrangians.  
- Automatic construction of the canonical/extended Hamiltonians (with fallbacks to user-provided H).  
- Primary and secondary constraint discovery and **first-/second-class** classification.  
- Global constraint matrix and conditional inversion when only second-class constraints remain.  
- Poisson and Dirac brackets, including gauge-fixed reduced dynamics (optional).  
- Clear console output of intermediate results for verification and debugging.

**Main functions (non-exhaustive):**
- `SolveSingular`, `SolveSingularS`, `SolveSingularH` — three variants with the **same inputs/outputs**; they differ only in internal strategy.  
- `PoissonBrackets` — Poisson bracket.  
- `DiracBrackets` — Dirac bracket.  

---

## Requirements

- **MATLAB** (R2021a or later recommended).  
- **Symbolic Math Toolbox**.   
- (Optional) **Live Editor** to run the included `.mlx` example interactively (comes with MATLAB).

> If you find a version incompatibility, please open an issue with your MATLAB release number.

---

## Installation

1. Download the toolbox file (`DiracFormalism - ToolBox.mltbx`) from this repository.  
2. Double-click it; confirm the installation.  
3. The functions will be available on your MATLAB path.

## Files in this repository

- **`DiracFormalism - ToolBox.mltbx`** — MATLAB toolbox package containing the functions. Install it and call the functions directly from your code.  
- **`guide.pdf`** — User guide describing the main functions, inputs/outputs, and usage tips.  
- **`examples.mlx`** — MATLAB Live Script showcasing worked examples, from simple toy models to systems with gauge fixing.

