# README

## 📑 Project Overview
This repository contains **four Jupyter Notebooks** that take you from raw data ➜ clean, engineered features ➜ three distinct, fully‑explained machine‑learning models.  
The work satisfies the course deliverable that **every model be trained, evaluated, and interpreted with *at least four* explainability techniques**.

| Notebook | Purpose |
|----------|---------|
| `01_Data_Preprocessing_EDA_FeatureEng.ipynb` | Loads the raw dataset, performs exploratory‑data analysis (EDA), handles missing values & outliers, scales/encodes features, and saves a cleaned feature matrix (`data/processed/clean_Xy.pkl`). |
| `02_Model_RF_Jilan_Ismail_202201997.ipynb` | Random Forest classifier + SHAP, LIME, PDP, permutation importance. |
| `03_Model_XGB_Jilan_Ismail_202201997.ipynb` | XGBoost classifier + SHAP, LIME, PDP, permutation importance. |
| `04_Model_MLP_Jilan_Ismail_202201997.ipynb` | Multilayer‑Perceptron + SHAP (DeepExplainer), LIME, Integrated Gradients, PDP. |

Each model notebook is self‑contained, but **all of them expect the pre‑processed file produced by Notebook 01**.

---

## 🗂️ Directory Structure
```text
project_root/
│
├── data/
│   ├── raw/                    # original CSV / Parquet files
│   └── processed/
│       └── clean_Xy.pkl        # created by Notebook 01
│
├── notebooks/
│   ├── 01_Data_Preprocessing_EDA_FeatureEng.ipynb
│   ├── 02_Model_RF_Jilan_Ismail_202201997.ipynb
│   ├── 03_Model_XGB_Jilan_Ismail_202201997.ipynb
│   └── 04_Model_MLP_Jilan_Ismail_202201997.ipynb
│
├── outputs/                    # figures, HTML exports, saved models (*.joblib)
├── requirements.txt
└── README.md                   # ← *you are here*
```

---

## ⚙️ Quick‑Start (5 Steps)
1. **Clone the repo**
   ```bash
   git clone https://github.com/<your‑org>/<your‑repo>.git
   cd <your‑repo>
   ```

2. **Create & activate a virtual environment**
   ```bash
   # Conda (recommended)
   conda env create -n ds253_env -f environment.yml
   conda activate ds253_env
   # or with pip:
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

3. **Launch Jupyter**
   ```bash
   jupyter lab
   ```

4. **Run Notebook 01 first**
   Open `01_Data_Preprocessing_EDA_FeatureEng.ipynb` and run all cells.  
   At the end you will see **“✅ Saved processed data to `data/processed/clean_Xy.pkl`”**.

5. **Run any model notebook**
   Open one of the model notebooks, run all cells, and inspect:
   * Cross‑validation metrics
   * Confusion matrix & classification report
   * **Four explainability blocks** (feature importance, PDP/ICE, SHAP summary, LIME local explanation, etc.)
   * Saved artefacts in `outputs/`

---

## 📦 Key Dependencies
Full list in `requirements.txt`.

| Package | Tested Version |
|---------|----------------|
| python | 3.11 |
| pandas | 2.2 |
| numpy  | 1.26 |
| scikit‑learn | 1.4 |
| xgboost | 2.0 |
| shap   | 0.44 |
| lime   | 0.3 |
| pdpbox | 0.3 |
| matplotlib / seaborn | latest |
| ipywidgets | 8.x |

---

## 📊 Explainability Checklist (per model)
| Technique | RF | XGB | MLP |
|-----------|----|-----|-----|
| Global feature importance | ✔ | ✔ | ✔ |
| Permutation importance | ✔ | ✔ | ✔ |
| Partial‑Dependence / ICE | ✔ | ✔ | ✔ |
| SHAP | ✔ | ✔ | ✔ |
| LIME | ✔ | ✔ | ✔ |
| Integrated Gradients | — | — | ✔ |

---

## 🆘 Troubleshooting
| Issue | Fix |
|-------|-----|
| `ModuleNotFoundError: shap_BiasAdd` | Run `pip install shap==0.44 tensorflow==2.15` and restart kernel. |
| Notebook freezes on big SHAP plots | Reduce sample size: set `n_samples = 100` in the SHAP cell. |
| “CUDA not found” | Verify `nvidia‑smi`; then install `xgboost` with `pip install xgboost‑cuda` (Linux only). |

---

## 👩‍🏫 Citation / Acknowledgements
* Data source: **[Add dataset citation]**  
* Libraries: scikit‑learn © Inria, XGBoost © Tianqi Chen et al., LIME © Marco Ribeiro et al., SHAP © Scott Lundberg et al.

---

## ✍️ Authors
* **Jilan Ismail (202201997)** – notebooks & report  
* **Team ML** – idea conception & EDA guidance

---

> **بالتوفيق!**  
> Run the notebooks in order and let the visualisations guide you. For issues, open an issue or ping the team.
