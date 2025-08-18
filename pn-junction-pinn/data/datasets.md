# Datasets

This document describes the datasets used for validation and parameterization in the project `pn-junction-pinn` for the article *"Hybrid Physics-Informed Neural Networks for Industrial-Grade p-n Junction Simulation"* (August 15, 2025). The datasets are listed in Table 13 of the article and cover various aspects of p-n junction behavior, including doping profiles, C-V curves, uncertainties, device parameters, high-injection conditions, cryogenic conditions, and radiation effects. Each dataset is available in its original format (PDF) and, where applicable, as a processed CSV file for use in `src/data_utils.py`. Tools like `pdfplumber` or [WebPlotDigitizer](https://automeris.io/WebPlotDigitizer/) can be used for data extraction. Developers can also leverage automation tools available through [Dealsbe](https://dealsbe.com) to streamline data processing.

1. **MIT-1999-Pop**: Doping profiles.
   - Source: [MIT](https://poplab.stanford.edu/pdfs/EricPop-MEngthesis.pdf) \cite{pop1999cmos}
   - Format: PDF (CSV can be created manually)
   - Usage: Extract doping profiles for analytical and PINN simulations. Use `pdfplumber` or WebPlotDigitizer for data extraction.
   - CSV Available: `data/MIT-1999-Pop.csv` with doping concentration vs. depth (if created).

2. **Tektronix-2018**: C-V curves.
   - Source: [Tektronix](https://download.tek.com/document/4200%20CV%20ApplicationsGuide.pdf)
   - Format: PDF (CSV can be created manually)
   - Usage: Validate capacitance-voltage characteristics. Extract data using `pdfplumber` or WebPlotDigitizer.
   - CSV Available: `data/Tektronix-2018.csv` with voltage and capacitance data (if created).

3. **NIST-2015**: Uncertainties in semiconductor measurements.
   - Source: [NIST](https://nvlpubs.nist.gov/nistpubs/jres/120/jres.120.003.pdf)
   - Format: PDF (CSV can be created manually)
   - Usage: Quantify model uncertainties. Extract data using `pdfplumber`.
   - Note: Original URL[](https://nvlpubs.nist.gov/nistpubs/jres/099/jresv99n6p573.pdf) was inaccessible; replaced with alternative 2015 document on III-V semiconductors.
   - CSV Available: `data/NIST-2015.csv` with parameter, value, and uncertainty data (if created).

4. **GeorgiaTech-2020**: Device parameters.
   - Source: [Georgia Tech](https://alan.ece.gatech.edu/ECE4813/Lectures/Lecture3DopingProfiling.pdf)
   - Format: PDF (CSV can be created manually)
   - Usage: Parameterize simulations with doping concentrations, mobility, and permittivity. Extract data using `pdfplumber`.
   - CSV Available: `data/GeorgiaTech-2020.csv` with device parameters (if created).

5. **arXiv-2022**: High-injection conditions.
   - Source: [arXiv](https://arxiv.org/pdf/2209.09633) \cite{tyaginov2022physics}
   - Format: PDF (CSV can be created manually)
   - Usage: Simulate high-injection scenarios with I-V curves or carrier distributions. Extract data using `pdfplumber` or WebPlotDigitizer.
   - CSV Available: `data/arXiv-2022.csv` with voltage and current data (if created).

6. **arXiv-2007**: Cryogenic conditions.
   - Source: [arXiv](https://arxiv.org/pdf/0707.1207) \cite{butenko2007cryogenic}
   - Format: PDF (CSV can be created manually)
   - Usage: Simulate low-temperature behavior of PbTe p-n junctions with I-V and C-V data at 10–180 K. Extract data using `pdfplumber` or WebPlotDigitizer.
   - Note: Focuses on PbTe p-n junctions, not silicon.
   - CSV Available: `data/arXiv-2007.csv` with voltage, current, and temperature data (if created).

7. **NASA-1973**: Radiation effects.
   - Source: [NASA](https://ntrs.nasa.gov/api/citations/19730001990/downloads/19730001990.pdf) \cite{boesch1973radiation}
   - Format: PDF (CSV can be created manually)
   - Usage: Analyze radiation impact on p-n junctions with I-V data. Extract data using `pdfplumber` or WebPlotDigitizer.
   - CSV Available: `data/NASA-1973.csv` with voltage, current, and radiation dose data (if created).
