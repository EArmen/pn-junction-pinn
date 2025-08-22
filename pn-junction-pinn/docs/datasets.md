# Open-Access Datasets

This work is committed to reproducibility and uses exclusively open-access data for training and validation.

---

## Summary of Data Sources

| Source | Key Parameters Provided | URL | License / Terms |
| :--- | :--- | :--- | :--- |
| Stanford POPLab (Pop, 1999) | Doping profiles, junction depth (~1.2 µm) | [Link](https://poplab.stanford.edu/pdfs/EricPop-MEngthesis.pdf) | Academic Use |
| Tektronix (2018) | C-V measurements (1 MHz, -5V to +5V) | Link | Application Guide |
| NIST (2015) | Measurement uncertainties (±3.5%) | [Link](https://nvlpubs.nist.gov/nistpubs/jres/120/jres.120.003.pdf) | Public Domain |
| Georgia Tech (2020) | Junction parameters | [Link](https://alan.ece.gatech.edu/ECE4813/Lectures/Lecture3DopingProfiling.pdf) | CC-BY 4.0 |
| arXiv:2209.09633 (2022) | High-injection condition data | [Link](https://arxiv.org/pdf/2209.09633) | Non-exclusive dist. |
| arXiv:0707.1207 (2007) | Cryogenic operation data (77K) | [Link](https://arxiv.org/pdf/0707.1207) | Non-exclusive dist. |
| NASA Tech Reports (1973) | Radiation effects (10 krad) | [Link](https://ntrs.nasa.gov/api/citations/19730001990/downloads/19730001990.pdf) | Public Domain |

---

## Data Integration Pipeline

### 1. Automated Data Fetching
Implemented in `src/data_utils.py`.

Example:
```python
import pdfplumber, requests

url = 'https://poplab.stanford.edu/pdfs/EricPop-MEngthesis.pdf'
response = requests.get(url)
with open('temp_profile.pdf', 'wb') as f:
    f.write(response.content)

with pdfplumber.open('temp_profile.pdf') as pdf:
    page = pdf.pages[10]
    table = page.extract_table()
```

### 2. Data Processing & Uncertainty
* Normalization and scaling for training
* Experimental uncertainties (e.g., ±8.7%) included for robustness  
Handled in `src/data/dataloader.py`.

### 3. Using Data in Code

```python
from src.data.dataloader import JunctionDataLoader

data_loader = JunctionDataLoader()
X_cv, y_cv = data_loader.get_cv_data(bias_range=(-5, 5), source='tektronix')
```

---

## License Compliance

All data usage complies with the original licenses. Please cite the original sources.
