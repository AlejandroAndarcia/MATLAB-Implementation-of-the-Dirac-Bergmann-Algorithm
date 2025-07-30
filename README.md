# MATLAB-Implementation-of-the-Dirac-Bergmann-Algorithm

**Brief description.**  
This MATLAB code automates the Dirac–Bergmann constraint formalism to analyze **singular** Lagrangian systems.

> **Acknowledgment.** Parts of this codebase and documentation were developed **with the assistance of ChatGPT**.

---

## Features

- Full Dirac–Bergmann workflow for symbolic Lagrangians.  
- Automatic construction of the canonical/extended Hamiltonians (with fallbacks to user-provided \(H\)).  
- Primary and secondary constraint discovery and **first-/second-class** classification.  
- Global constraint matrix \(W_{ab}=\{\phi_a,\phi_b\}\) and conditional inversion when only second-class constraints remain.  
- Poisson and Dirac brackets, including gauge-fixed reduced dynamics (optional).  
- Clear console output of intermediate results for verification and debugging.

**Main functions (non-exhaustive):**
- `SolveSingular`, `SolveSingularS`, `SolveSingularH` — three variants with the **same inputs/outputs**; they differ only in internal strategy.  
- `PoissonBrackets` — canonical Poisson bracket \(\{F,G\}\) given coordinate names.  
- `DiracBrackets` — Dirac bracket \(\{q_i,P_j\}_D\) using \(M^{-1}\) from second-class constraints.  

---

## Requirements

- **MATLAB** (R2021a or later recommended).  
- **Symbolic Math Toolbox**.   
- (Optional) **Live Editor** to run the included `.mlx` example interactively (comes with MATLAB).

> If you find a version incompatibility, please open an issue with your MATLAB release number.

---

## Installation

1. Download the toolbox file (e.g., `DiracConstraints.mltbx`) from this repository.  
2. Double-click it or drag-and-drop into MATLAB; confirm the installation.  
3. The functions will be available on your MATLAB path.

## Files in this repository

- **`DiracConstraints.mltbx`** — MATLAB toolbox package containing the functions. Install it and call the functions directly from your code.  
- **`guide.pdf`** — User guide describing the main functions, inputs/outputs, and usage tips.  
- **`examples.mlx`** — MATLAB Live Script showcasing several worked examples, from simple toy models to systems with gauge fixing.

> File names above are illustrative; adjust to match your actual filenames.

---

## Quick start

```matlab
% Symbols (declare all as real)
syms x y P_x P_y real
syms k real
V = k/2*(x^2 + y^2);

% Lagrangian (use _dot suffix for velocities)
syms x_dot y_dot real
L = 1/2*(x_dot^2 + y_dot^2) - V;

% Option A: let the code build H_can
H_guess  = 0;               % automatic canonical Hamiltonian
gaugeFix = {};              % no gauge
[H_e, allRestrictions, WMatrix, DiracBracketsInd, eqMotion] = ...
    SolveSingular(L, H_guess, gaugeFix, 'x', 'y');

% Option B: provide your own H
H_user = 1/2*(P_x^2 + P_y^2) + V;
[H_e, allRestrictions, WMatrix, DiracBracketsInd, eqMotion] = ...
    SolveSingular(L, H_user, gaugeFix, 'x', 'y');
