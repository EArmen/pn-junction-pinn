# Methodology: Physical Equations and PINN Architecture

This document outlines the core physics and machine learning principles behind the hybrid framework. It connects the implementation in the `src/` directory to the theory presented in the paper.

---

## 1. Analytical Foundations

The base model is the classic Shockley depletion approximation for an abrupt p-n junction.

### Core Equations

* Poisson's Equation:
  $$\frac{d^2\phi}{dx^2} = -\frac{\rho(x)}{\varepsilon \varepsilon_0}$$

* Charge Density ($\rho$):
  $$
  \rho(x) =
    \begin{cases}
      -qN_a & x < 0 \\
      +qN_d & x > 0
    \end{cases}
  $$

* Built-in Potential ($V_{bi}$):
  $$V_{bi} = \frac{kT}{q} \ln\left(\frac{N_a N_d}{n_i^2}\right)$$

* Depletion Width ($d$):  
  For a symmetric junction ($N_a = N_d = N$):
  $$d = \sqrt{\frac{4\varepsilon\varepsilon_0 V_{bi}}{qN}}$$

Implementation: These equations are implemented in `src/analytical_model.py`.

---

## 2. Numerical Solver

To overcome the limitations of the analytical model, we solve the Poisson equation numerically using a finite-difference method.

Finite-Difference Discretization:
$$\frac{\phi_{i+1} - 2\phi_i + \phi_{i-1}}{\Delta x^2} = -\frac{\rho_i}{\varepsilon \varepsilon_0}$$

This results in a system of linear equations $A \cdot \phi = b$, which is solved efficiently.  
Implementation: See `src/numerical_solver.py`.

---

## 3. Physics-Informed Neural Network (PINN)

The PINN learns to approximate the solution $\phi(x)$ while automatically satisfying Poisson's equation.

### Architecture

Defined in `src/pinn/model.py`:

1. Inputs: $x$ coordinate (+ bias $V$ for multi-case models)
2. Fourier Feature Encoding: $\gamma(v) = [\cos(2\pi Bv), \sin(2\pi Bv)]$
3. Residual Blocks: Deep MLP (5 layers × 256 units) with Swish activation + skip connections
4. Multi-Head Output: Predicts $\phi$, $E$, and $C$ simultaneously

### Loss Function

$$\mathcal{L} = \alpha(t)\mathcal{L}_{\text{physics}} + \beta(t)\mathcal{L}_{\text{data}} + \gamma\mathcal{L}_{\text{reg}}$$

* **Data Loss:** MSE against numerical or TCAD data
* **Physics Loss:** Poisson residual MSE
* **Adaptive Weights:** Dynamically balanced using an annealing schedule

Training loop: See `src/pinn/train.py`.

---

## 4. Hybrid Workflow

The workflow combines three layers:

1. Analytical: quick approximations
2. Numerical: high-fidelity ground truth
3. PINN: fast inference after training
