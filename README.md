# 📊 Predictive Modeling and CDSS for SDF Markers

This repository contains the implementation code for our research paper on predictive modeling of **Sperm DNA Fragmentation (SDF)** markers and the design of a **Clinical Decision Support System (CDSS)**. The analysis was conducted on a clinical dataset through a structured workflow using Jupyter Notebooks.

---

## 🗂 Repository Structure

### `data/`  
Raw and processed datasets, including:
- `raw_data.xlsx`: raw data from the fertility center.
- `analyzed_data.pkl`: Preprocessed training-validation set for SDF benchmark and CDSS training.
- `analyzed_test_data.pkl`: Preprocessed test set for SDF benchmark and CDSS evaluation.

### `notebooks/`  
Contains the complete analysis pipeline:

- `01_split_data.ipynb`: Initial train-test split with class balancing and distribution checks.  
- `02_data_cleaning.ipynb`: Cleaning, imputation, and dataset preparation.  
- `03_naive_benchmark.ipynb`: Baseline regression with dummy models.  
- `04_EDA.ipynb`: Exploratory Data Analysis and visualizations.  
- `05_model_benchmarking.ipynb`: ML models for SDF prediction + SHAP explanations.  
- `06_cdss_design.ipynb`: CDSS development for low-risk patient identification.  
- `07_error_analysis.ipynb`: Final error and explainability analysis.  

### `outputs/models/`  
Trained models saved via `joblib`, used in benchmarking and CDSS.

---

## ✅ Requirements

- Python ≥ 3.8  
- Jupyter Notebook  
- Key libraries: `pandas`, `numpy`, `scikit-learn`, `random forests`,`xgboost`, `lightgbm`, `catboost`, `optuna`, `shap`, `matplotlib`, `seaborn`, `scipy`, `joblib`

---

## 🔄 Workflow

To reproduce the analysis end-to-end:

### 1. Data Preparation

Open and run `01_split_data.ipynb`:
- Splits raw data into train/validation and hold-out test sets.
- Ensures stratified class distribution and performs KS tests.

Then run `02_data_cleaning.ipynb`:
- Handles missing values, performs KNN imputation, and saves cleaned data.

### 2. Baseline and EDA

Run:
- `03_naive_benchmark.ipynb`: Establish DummyRegressor baselines.
- `04_EDA.ipynb`: Perform visual analysis, outlier detection, and feature binning.

### 3. Model Benchmarking

Open `05_model_benchmarking.ipynb`:
- Trains and evaluates multiple regression models:  
  Linear, Ridge, Random Forest, XGBoost, CatBoost, LightGBM  
- **To load trained models**, go to Part 4 and use `joblib.load()` on files in `outputs/models/`.

### 4. CDSS Evaluation

Run `06_cdss_design.ipynb`:
- Load `quantile_models.pkl` from `outputs/models/`
- Feed `analyzed_test_data.pkl` from `data/` into the quantile model
- Generate the clinician-friendly decision table

### 5. Error and Explainability Analysis

Finally, run `07_error_analysis.ipynb`:
- Analyze prediction errors, perform statistical tests, and visualize SHAP outputs

---

## 📌 Notes

- Follow the notebooks **sequentially from `01` to `07`** for full pipeline execution.
- All key models and intermediate outputs are saved for reproducibility.
- Results are based on clinically validated thresholds and guidelines.



