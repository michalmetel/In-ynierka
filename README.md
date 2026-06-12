# Drug delivery systems and predictive modeling of anticancer therapy efficacy

My engineering thesis project combining wet lab biomaterials work with machine learning to study silver nanoparticle (AgNPs) cytotoxicity against ovarian cancer cells.

---

## Overview

The project has two parts:

**Lab work** — synthesis and characterization of AgNPs and AgNPs loaded with carboplatin (AgNPs+CPT), followed by in vitro cytotoxicity testing on the OVCAR-3 ovarian cancer cell line (LDH assay + Live/Dead staining).

**Predictive modeling** — linear regression model predicting cancer cell viability based on AgNPs concentration, drug concentration, and incubation time. Built on a manually curated dataset of 50 observations from published literature.

The modeling part was done entirely by me. The lab part was done in collaboration with the biomaterials research group at my university.

---

## Repository structure

```
├── linear_regression.ipynb   # Main notebook: data preprocessing, model, evaluation
├── regression1.ipynb         # Exploratory analysis
├── regression2.ipynb         # Additional experiments
└── data/
    └── dataset.csv           # Not included — see Data section below
```

---

## Model

Linear regression trained with scikit-learn.

**Features:**
- `log_AgNPs` — log₁₀ of AgNPs concentration (µg/ml)
- `Incubation [h]` — incubation time in hours
- `Drug` — drug concentration (µg/ml)
- `logC_x_time` — interaction term: log₁₀(C) × incubation time

**Target:** Cell viability (%)

**Performance:** R² = 24.49, MSE = 0.36

The model captures general trends but is not suitable for precise predictions — small dataset, heterogeneous sources, and linear architecture are the main limitations.

---

## Data

Dataset is **not included** due to mixed origin — part from my own experiments, part manually extracted from published literature. To reproduce, place `dataset.csv` in the `data/` folder with columns:

```
AgNPs;Drug;Incubation [h];Viability [%]
```

Concentrations unified to µg/ml.

Key literature sources used for the dataset:

| DOI |
|-----|
| https://doi.org/10.2147/IJN.S135482 |
| https://doi.org/10.1186/s13048-022-01056-3 |
| https://doi.org/10.2147/IJN.S111279 |
| https://doi.org/10.3390/nano8080627 |
| https://doi.org/10.1155/2017/5107485 |
| https://doi.org/10.3390/ijms17122077 |
| https://doi.org/10.3390/ijms19030710 |

---

## Requirements

```
python >= 3.12
pandas
numpy
matplotlib
scikit-learn
```

```bash
pip install pandas numpy matplotlib scikit-learn
```

---

## License

MIT
