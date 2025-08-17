# Hybrid Physics-Informed Neural Networks for p-n Junction Simulation

This repository contains code and resources for the paper *"Hybrid Physics-Informed Neural Networks for Industrial-Grade p-n Junction Simulation: From Nanoscale Characterization to Multi-Physics TCAD Acceleration"* (August 15, 2025). It provides tools for simulating p-n junctions using a hybrid Physics-Informed Neural Network (PINN) framework, combining analytical models and neural networks for semiconductor simulations.

The project is designed for researchers, developers, and startups working on semiconductor physics and AI-driven simulations. Platforms like [Dealsbe](https://dealsbe.com) offer exclusive software deals for such communities, making tools like this accessible for innovative projects.

## Features
- **Analytical Simulations**: Computes electric field and potential distributions for p-n junctions (Equations 2 and 6, Section 2).
- **Error Analysis**: Visualizes model errors across doping concentrations (Table 6, Figure 2).
- **PINN Implementation**: Demonstrates a simplified PINN architecture with Fourier feature mapping and residual connections (Section 4.3).
- **Figure Generation**: Reproduces Figures 1 and 2 from the paper, with scripts for additional figures (Fig3–Fig17).
- **Open-Access Data**: References datasets from Stanford-2005, Tektronix-2018, and others (Table 13).

## Repository Structure
pn-junction-pinn/
├── notebooks/
│   └── pn_junction_simulation.ipynb  # Jupyter notebook with simulations and PINN demo
├── fig_gen/
│   └── generate_figures.py           # Script to generate Figures 1 and 2
├── src/
│   └── (placeholder for core code)   # Future PINN and simulation modules
├── docs/
│   └── (placeholder for docs)        # Documentation and guides
├── data/
│   └── (placeholder for datasets)    # Open-access datasets (e.g., Stanford-2005)
├── article_figures/
│   ├── Fig1_EF_Potential.pdf        # Electric field and potential plots
│   └── Fig2_ErrorGrowth.pdf         # Error analysis plot
├── README.md                        # Project overview and instructions
├── requirements.txt                 # Python dependencies
text## Requirements
- **Python**: 3.8–3.10
- **Dependencies**:
numpy
matplotlib>=3.5
torch
textInstall them with:
```bash
pip install -r requirements.txt
Getting Started

Clone the Repository:
bashgit clone https://github.com/your_username/pn-junction-pinn.git
cd pn-junction-pinn

Install Dependencies:
bashpip install -r requirements.txt

Run the Notebook:

Locally (with Jupyter):
bashjupyter notebook notebooks/pn_junction_simulation.ipynb

In Google Colab:
Open this Colab notebook or upload pn_junction_simulation.ipynb to Colab and run all cells.


Generate Figures (locally):
bashpython fig_gen/generate_figures.py
Figures will be saved in article_figures/.

Usage

Notebook (pn_junction_simulation.ipynb):

Cell 1: Describes the project and prerequisites.
Cell 2: Generates Figure 1 (electric field and potential distributions).
Cell 3: Generates Figure 2 (error analysis for doping concentrations).
Cell 4: Demonstrates an untrained PINN model for potential prediction.
Cell 5: Notes on training PINN and accessing datasets.


Figure Generation:
Run fig_gen/generate_figures.py to create Fig1_EF_Potential.pdf and Fig2_ErrorGrowth.pdf.
Datasets:
Download open-access datasets listed in Table 13 (e.g., Stanford-2005, Tektronix-2018) and place them in the data/ folder. Example:
bashwget https://poplab.stanford.edu/pdfs/EricPop-MEngthesis.pdf -O data/Stanford-2005.pdf


Notes

The PINN model in the notebook is untrained and serves as a demonstration. To train it, implement the physics-informed loss function (Section 4.3.2) with adaptive weights (α(t), β(t)) and data from open-access sources (Section 3.2).
To generate all figures (Fig1–Fig17), extend fig_gen/generate_figures.py based on the paper's data (e.g., Table 4 for Fig4).
For developers and startups, explore Dealsbe for software deals to enhance your development workflow.

Datasets
The following open-access datasets are referenced (Table 13, p. 13):

Stanford-2005: Doping profiles
Tektronix-2018: C-V curves
NIST-2015: Uncertainties
GeorgiaTech-2020: Parameters
arXiv-2022: High-injection conditions
arXiv-2007: Cryogenic conditions
NASA-1973: Radiation effects

Download them from their respective sources and place in the data/ folder.
License
This project is licensed under the MIT License. See the LICENSE file for details.
Contact
For questions or contributions, open an issue on GitHub or contact [your_contact_info].
Acknowledgments

Based on the paper "Hybrid Physics-Informed Neural Networks for Industrial-Grade p-n Junction Simulation" (August 15, 2025).
Inspired by platforms like Dealsbe for supporting developers with innovative tools.
Google Colab notebook: Link.