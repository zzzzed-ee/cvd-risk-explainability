# Cardiovascular Disease Risk & Model Explainability

Predicting Cardiovascular Disease (CVD) using routine medical examination data and evaluating the driving factors behind the predictions. 

This project explores a fundamental diagnostic question: **How well can routine measurements predict CVD, and which type of factor drives those predictions—immutable traits, physiological vitals, or lifestyle choices?** By utilizing Random Forest classification and SHAP (SHapley Additive exPlanations), this repository moves beyond simple accuracy metrics to provide a transparent, interpretable ablation study of patient health risks.

## Project Structure

This repository follows a standard data science project structure:

```text
├── data/
│   ├── raw/                 # Original dataset (cardio_train.csv)
│   └── processed/           # Cleaned data with engineered features
├── notebooks/               # Jupyter notebooks (e.g., Final_Code_updated.ipynb)
├── outputs/                 # Exported SHAP plots, ROC curves, and ablation tables
├── .gitignore               # Ignored files and directories
├── README.md                # Project documentation
└── requirements.txt         # Required Python libraries
```

## Methodology

1. **Data Cleaning & Engineering:**
   * Removed physiologically impossible values (e.g., extreme blood pressure readings, negative values).
   * Engineered practical clinical features, including Age (in years), BMI, and Pulse Pressure.
2. **Modeling Pipeline:**
   * **Baseline Model:** Decision Tree Classifier to establish initial predictive performance.
   * **Advanced Model:** Random Forest Classifier (tuned with `RandomizedSearchCV`) evaluated using Accuracy, ROC-AUC, and Confusion Matrices.
3. **Model Explainability (SHAP & Ablation):**
   * Features were grouped into three distinct categories: **Immutable Traits** (Age, Gender), **Physiological Vitals** (Blood Pressure, BMI, Cholesterol, Glucose), and **Lifestyle Choices** (Smoking, Alcohol, Activity).
   * Conducted a feature-group ablation study to test the isolated predictive power of each category.
   * Aggregated SHAP values by category to quantify the percentage share of the model's decision-making process driven by each group.

## Key Findings

* **Physiological Vitals Dominate:** The ablation study and grouped SHAP analysis reveal that physiological measurements (specifically systolic blood pressure and cholesterol) heavily outweigh lifestyle choices in driving the model's immediate predictions.
* **Model Performance:** The Random Forest pipeline successfully handles the coarse, heavily-rounded nature of the raw clinical measurements to deliver robust ROC-AUC scores.

## Getting Started

### Prerequisites
Ensure you have Python 3.8+ installed. The primary libraries used in this project are `pandas`, `numpy`, `scikit-learn`, `shap`, `seaborn`, and `matplotlib`.

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/zzzzed-ee/cvd-risk-explainability.git
   cd data-project
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Analysis
1. Place the raw Kaggle dataset (`cardio_train.csv`) into the `data/raw/` directory.
2. Launch Jupyter Notebook or Jupyter Lab:
   ```bash
   jupyter notebook
   ```
3. Open `notebooks/Final Code.ipynb` and run the cells sequentially to execute the data cleaning, model training, and SHAP visualizations.
