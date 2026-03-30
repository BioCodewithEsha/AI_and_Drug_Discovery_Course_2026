🧬 AChE QSAR Modeling using Machine Learning

A machine learning–based Quantitative Structure–Activity Relationship (QSAR) model for predicting Acetylcholinesterase (AChE) inhibitory activity using molecular descriptors calculated through PaDEL-Descriptor.
This project includes complete data preprocessing, descriptor engineering, Lipinski filtering, statistical testing, model benchmarking, Random Forest optimization, and final model evaluation.

📁 Project Structure
📦 AChE_QSAR_Model
 ┣ 📄 AChE_QSAR_Modelling.ipynb
 ┣ 📄 mannwhitney_summary.csv
 ┣ 📄 descriptor_data.csv
 ┣ 📄 best_model.pkl (optional if added)
 ┣ 📄 README.md
 ┗ 📄 requirements.txt
📌 Project Overview

This project builds a regression QSAR model to predict pIC50 values of molecules targeting Acetylcholinesterase (AChE).
Key components include:

✔ Data Cleaning & Preprocessing
Removal of missing values
Log transformation → pIC50 computation
Lipinski Rule of 5 filtering
Handling outliers
✔ Molecular Descriptor Calculation

Using PaDELPy, generating:

1444 2D descriptors
431 3D descriptors
881 PubChem fingerprints
✔ Statistical Analysis

Performed Mann–Whitney U-tests to compare descriptor distributions for active vs. inactive molecules.
Output saved in:
mannwhitney_summary.csv

✔ Machine Learning Modeling

Automated model benchmarking using LazyPredict over 40+ regression algorithms.

✔ Best Model

RandomForestRegressor

R² Score: 0.68
Ranked: 1 out of 42 models
Tuned with hyperparameters
Exported as best_model.pkl
🚀 Features
Full QSAR workflow (end-to-end)
ADME/Lipinski filtering
Descriptor generation via PaDELPy
Statistical significance testing
Automatic model selection
Hyperparameter tuning
Exportable model for deployment
🧪 How to Run the Notebook
1. Install dependencies
pip install -r requirements.txt
2. Run PaDEL-Descriptor
java -jar PaDEL-Descriptor.jar -dir molecules/ -file descriptors.csv
3. Open the Jupyter Notebook
jupyter notebook AChE_QSAR_Modelling.ipynb
📊 Model Performance Summary
Metric	Score
Best Model	RandomForestRegressor
R² Score	0.6834
Improvement After Tuning	0.02%
Ranking	1 / 42 models
📦 Dataset

The dataset consists of curated bioactivity records for AChE inhibitors, including:

Canonical SMILES
Experimental IC50 values
Calculated pIC50
Physicochemical descriptors

(Data source not included in repository due to size restrictions)

🔍 Mann–Whitney U Statistical Results

Key descriptors such as MW, LogP, HBA, HBD, and pIC50 show significant distribution differences, confirming biological relevance.

🛠 Tech Stack
Python 3.10+
RDKit
PaDELPy (PaDEL Descriptor Engine)
Pandas, NumPy, SciPy
Scikit-learn
LazyPredict
Matplotlib / Seaborn
📥 Model Export

Save trained model:

import joblib
joblib.dump(model, "best_model.pkl")

Load later:

model = joblib.load("best_model.pkl")
