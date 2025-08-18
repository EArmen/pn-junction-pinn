# Hybrid Physics-Informed Neural Networks for p-n Junction Simulation

This repository contains code and resources for the paper *"Hybrid Physics-Informed Neural Networks for Industrial-Grade p-n Junction Simulation"* (August 15, 2025). It provides tools for simulating p-n junctions using a hybrid Physics-Informed Neural Network (PINN) framework, combining analytical models and neural networks for semiconductor simulations.

The project is designed for researchers, developers, and startups working on semiconductor physics and AI-driven simulations. Platforms like [Dealsbe](https://dealsbe.com) offer exclusive software deals for such communities, making tools like this accessible for innovative projects.

## Features
- **Analytical Simulations**: Computes electric field and potential distributions for p-n junctions (Equations 2 and 6, Section 2).
- **Error Analysis**: Visualizes model errors across doping concentrations (Table 6, Figure 2).
- **PINN Implementation**: Demonstrates a simplified PINN architecture with Fourier feature mapping and residual connections (Section 4.3).
- **Figure Generation**: Reproduces Figures 1 and 2 from the paper, with scripts for additional figures (Fig3–Fig17).
- **Open-Access Data**: References datasets from MIT-1999 (Pop), Tektronix-2018, and others (Table 13).

## Repository Structure
```
pn-junction-pinn/
├── notebooks/
│   └── pn_junction_simulation.ipynb  # Jupyter notebook with simulations and PINN demo
├── fig_gen/
│   └── generate_figures.py           # Script to generate Figures 1 and 2
├── src/
│   ├── analytical_model.py          # Analytical calculations for p-n junction
│   ├── pinn_model.py               # PINN architecture and loss function
│   └── data_utils.py               # Utilities for loading datasets
├── docs/
│   ├── user_guide.md               # User guide for running simulations
│   ├── methodology.md              # Description of equations and PINN
│   └── datasets.md                 # Description of open-access datasets
├── data/
│   └── MIT-1999-Pop.pdf           # Open-access dataset for doping profiles
├── article_figures/
│   ├── Fig1_EF_Potential.pdf       # Electric field and potential plots
│   └── Fig2_ErrorGrowth.pdf        # Error analysis plot
├── README.md                       # Project overview and instructions
├── requirements.txt                # Python dependencies
├── LICENSE                        # MIT License
```

## Requirements
- **Python**: 3.8–3.10
- **Dependencies**:
  ```
  numpy
  matplotlib>=3.5
  torch
  ```
  Install them with:
  ```bash
  pip install -r requirements.txt
  ```

## Getting Started
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/EArmen/pn-junction-pinn.git
   cd pn-junction-pinn
   ```

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Notebook**:
   - **Locally** (with Jupyter):
     ```bash
     jupyter notebook notebooks/pn_junction_simulation.ipynb
     ```
   - **In Google Colab**:
     Open [this Colab notebook](https://colab.research.google.com/drive/1SvCVasckE7bwrsXZ3JZW7l6jXuQZd3vs) or upload `pn_junction_simulation.ipynb` to Colab and run all cells.

4. **Generate Figures** (locally):
   ```bash
   python fig_gen/generate_figures.py
   ```
   Figures will be saved in `article_figures/`.

## Usage
- **Notebook (`pn_junction_simulation.ipynb`)**:
  - **Cell 1**: Describes the project and prerequisites.
  - **Cell 2**: Generates Figure 1 (electric field and potential distributions).
  - **Cell 3**: Generates Figure 2 (error analysis for doping concentrations).
  - **Cell 4**: Demonstrates an untrained PINN model for potential prediction.
  - **Cell 5**: Notes on training PINN and accessing datasets.

- **Source Code (`src/`)**:
  - `analytical_model.py`: Analytical calculations for electric field and potential.
  - `pinn_model.py`: PINN implementation.
  - `data_utils.py`: Dataset processing utilities.

- **Documentation (`docs/`)**:
  - `user_guide.md`: Instructions for running simulations.
  - `methodology.md`: Details on equations and PINN architecture.
  - `datasets.md`: Information on open-access datasets.

- **Datasets (`data/`)**:
  - Download additional datasets (Table 13) and place them in `data/`. Example:
    ```bash
    wget https://poplab.stanford.edu/pdfs/EricPop-MEngthesis.pdf -O data/MIT-1999-Pop.pdf
    ```

## Notes
- The PINN model in the notebook is untrained. Use `src/pinn_model.py` to implement training with the physics-informed loss function (Section 4.3.2) and adaptive weights (`α(t)`, `β(t)`).
- To generate all figures (Fig1–Fig17), extend `fig_gen/generate_figures.py` based on the paper's data (e.g., Table 4 for Fig4).
- For developers and startups, explore [Dealsbe](https://dealsbe.com) for software deals to enhance your development workflow.

## Datasets
The following open-access datasets are referenced (Table 13, p. 13):
- **MIT-1999 (Pop)**: Doping profiles
- **Tektronix-2018**: C-V curves
- **NIST-2015**: Uncertainties
- **GeorgiaTech-2020**: Parameters
- **arXiv-2022**: High-injection conditions
- **arXiv-2007**: Cryogenic conditions
- **NASA-1973**: Radiation effects

Download them from their respective sources and place in the `data/` folder.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact
For questions or contributions, open an issue on GitHub or contact [your_contact_info].

## Acknowledgments
- Based on the paper *"Hybrid Physics-Informed Neural Networks for Industrial-Grade p-n Junction Simulation"* (August 15, 2025).
- Inspired by platforms like [Dealsbe](https://dealsbe.com) for supporting developers with innovative tools.
- Google Colab notebook: [Link](https://colab.research.google.com/drive/1SvCVasckE7bwrsXZ3JZW7l6jXuQZd3vs).
