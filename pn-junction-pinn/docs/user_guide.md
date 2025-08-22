# User Guide: Running p-n Junction Simulations

This guide provides step-by-step instructions to get started with the simulation framework.

---

## Quick Start (Google Colab - Recommended for first time users)

The easiest way to run the code without any local installation is using our Google Colab notebook. It provides a pre-configured environment with all dependencies.

1. **Open the Notebook:**  
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SvCVasckE7bwrsXZ3JZW716jXuQZd3vs)

2. **Run All Cells:**
   - In the Colab menu, click `Runtime` → `Run all`.
   - This will install all packages, download datasets, and execute the entire simulation pipeline.

3. **View Results:**
   - Generated figures (e.g., electric field, potential, error analysis) will be displayed in the notebook.
   - You can download them from the Colab file browser (left sidebar).

---

## Local Installation (For advanced users)

For greater control and faster repeated runs, you can set up a local environment.

### Prerequisites
- **Python 3.8** or newer
- `pip` (Python package manager)
- *(Optional but recommended)* **NVIDIA GPU** with CUDA support for accelerated PINN training.

### 1. Clone the Repository
```bash
git clone https://github.com/EArmen/pn-junction-pinn.git
cd pn-junction-pinn
```

### 2. Install Dependencies
Install all required Python packages from the `requirements.txt` file:
```bash
pip install -r requirements.txt
```

### 3. Run Simulations
The project is modular. You can run different parts of the hybrid workflow.

**Run the Analytical Model (Shockley approximation)**
```bash
python src/analytical_model.py --doping 1e17 --v_bi 0.7
```

**Run the Numerical Solver (High-fidelity)**
```bash
python src/numerical_solver.py --doping 1e18 --v_bi 0.8 --mesh_points 1000
```

**Train a PINN model**
```bash
python src/pinn/train.py --config configs/pinn_config.yaml
```

**Use a pre-trained PINN for fast prediction**
```bash
python src/pinn/inference.py --model_path models/pretrained_finfet_5nm.pt --voltage 0.5
```

### 4. Reproduce All Paper Figures
To generate all plots from the manuscript, run:
```bash
python fig_gen/generate_figures.py
```
All figures will be saved as PDFs in the `article_figures/` directory.

---

## Getting Help

- **Browse the code:** The `src/` directory is well-commented.
- **Read the methodology:** See `methodology.md` for theoretical background.
- **Report issues:** If you find a bug, please open an issue on GitHub.
