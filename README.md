# AI_and_Drug_Discovery_Course_2026 — EGFR QSAR Data Curation

This repository contains a **Google Colab / Jupyter notebook** for **QSAR dataset curation** using **ChEMBL bioactivity data** for the **EGFR** target. The workflow retrieves IC50 measurements, cleans and standardizes the dataset, assigns simple bioactivity classes, visualizes distributions, and exports curated CSV files for downstream QSAR modeling.

Open in Colab:
- [Assignment 2 QSAR Data Curation](https://colab.research.google.com/github/BioCodewithEsha/AI_and_Drug_Discovery_Course_2026/blob/main/Assignment_2_QSAR_data_curation.ipynb)

----------------------------------------------------------

### 1) Install and import dependencies
The notebook installs and uses:
- `chembl_webresource_client` — query ChEMBL  
- `pandas` — data handling  
- `matplotlib`, `seaborn` — plotting  
- `rdkit` — SMILES parsing and molecule rendering  

### 2) Fetch bioactivity data from ChEMBL
- Searches ChEMBL targets for **EGFR**  
- Selects the first matching target and extracts its `target_chembl_id`  
- Queries **IC50** activities for that target  

### 3) Build a curated QSAR table
The notebook:
- Converts retrieved records into a DataFrame  
- Keeps only key fields:
  - `molecule_chembl_id`
  - `canonical_smiles`
  - `standard_type`
  - `standard_value`
  - `standard_units`  
- Drops rows with missing SMILES or activity values  
- Converts activity values to numeric  
- Standardizes units by converting **nM → µM**  
- Removes duplicates per molecule (`molecule_chembl_id`)  
- Saves curated dataset  

**Output file created:**  
- `QSAR_EGFR_data.csv`  

### 4) Assign bioactivity classes (simple thresholds)
A helper function classifies IC50 values (in µM) into:
- **active**: IC50 ≤ `1 µM`  
- **inactive**: IC50 ≥ `10 µM`  
- **intermediate**: otherwise  

### 5) Visualize the dataset
The notebook produces:
- Histogram of IC50 values (µM)  
- Bar plot of bioactivity class counts  
- RDKit grid image of the first few molecules  

### 6) Export a preprocessed dataset
Final export:  
- `QSAR_EGFR_preprocessed.csv` — includes `bioactivity_class`  

---

## Outputs

After running the notebook, you should have:
- `QSAR_EGFR_data.csv` — cleaned + unit-standardized IC50 dataset (deduplicated)  
- `QSAR_EGFR_preprocessed.csv` — same dataset including `bioactivity_class`  

-------------------------------------------------------------------------------------------------------------------------------
