# Enterprise Data Engineering: Advanced EDA & Feature Engineering

**Author:** Tanishq Khanna  
**Education:** B.Tech (VLSI-A), Guru Gobind Singh Indraprastha University (GGSIPU)  
**Program:** DecodeLabs Industrial Training (Batch 2026)

## 📌 Project Overview
This project focuses on the structural engineering of mathematical truth for machine learning algorithms. Moving beyond basic qualitative reasoning, this pipeline transforms raw, chaotic data into a mathematically clean, production-ready dataset using an Input-Process-Output (IPO) architecture. 

## ⚙️ Phase 1: Securing Input Fidelity
* **Missing Data Imputation:** Handled missingness using strict statistical thresholds to mitigate MCAR and MAR scenarios (Row deletion for < 5%, Global Median/Mode for 5%-20%, and K-Nearest Neighbors for > 20%).
* **Outlier Neutralization:** Isolated statistical anomalies using the Interquartile Range (IQR) bounds. Capped values via `numpy.clip()` to preserve sequential integrity and data volume without destroying rows.

## 🚀 Phase 2: Vectorized Computation Engine
* **Performance Optimization:** Abandoned standard dynamic loops in favor of highly optimized, block-allocated RAM operations via Pandas and NumPy.
* **Coordinate Mapping:** Mapped distinct categories into orthogonal coordinate axes using One-Hot Encoding to prevent synthetic spatial hierarchy.
* **Collinearity Eradication:** Built an absolute correlation matrix and systematically dropped multicollinear features (Pearson > 0.80) based on their relative weakness to the target variable to stabilize OLS parameters.
* **Feature Engineering:** Extracted 3 highly predictive features to provide high-quality fuel for downstream estimators.

## 🛡️ Phase 3: Structural Contracts & Scaling
* **Runtime Validation:** Enforced strict data contracts at runtime using **Pandera** (`@pa.check_io`) to prevent silent data corruption and collect diagnostic failure logs.
* **Feature Store Integration:** Addressed Training-Serving Skew by designing the foundation for a central feature store (**Feast**) to ensure absolute point-in-time correctness.
* **Dual-Store Output:** Exported the final validated pipeline to a highly optimized **Parquet** format for offline batch querying.

## 🛠️ Tech Stack
* **Languages:** Python
* **Libraries:** Pandas, NumPy, Scikit-Learn, Pandera, Feast
* **Environment:** Google Colab


# The Repository Folder Structure

DecodeLabs-Data-Science-Project-1/
├── data/
│   ├── raw_dataset.csv             # Your initial uncleaned data
│   └── cleaned_dataset.parquet     # The final validated output
├── notebooks/
│   └── Project_1_Advanced_EDA.ipynb # Your Colab notebook
├── feature_repo/                   # (Optional) If you completed the Feast integration
│   ├── features.py
│   └── feature_store.yaml
├── requirements.txt                # List of libraries (pandas, numpy, pandera, feast)
└── README.md                       # The front page of your project
