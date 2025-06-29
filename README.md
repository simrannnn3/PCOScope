# PCOScope

PCOScope is a machine-learning-based diagnostic and explainability toolkit designed to assist in the early prediction of Polycystic Ovary Syndrome (PCOS) using clinical and ultrasound data. The project implements supervised classification models to predict PCOS presence and explores explainable AI (XAI) methods to increase transparency of model decisions.

---

## Problem Statement

PCOS is a common hormonal disorder among women of reproductive age. Early prediction and explanation of PCOS patterns can help guide timely treatment. This project leverages a real-world medical dataset to build an interpretable machine learning pipeline for PCOS diagnosis, including potential markers related to infertility.

---

## Dataset

- **Source**: PCOS dataset (without infertility) + infertility data (merged)
- **Format**: `.xlsx` and `.csv`
- **Features**: 45 clinical, hormonal, and ultrasound attributes
- **Target**: PCOS diagnosis (`PCOS (Y/N)`)

---

## Technical Overview

### Data Preprocessing

- Loaded data from Excel and CSV
- Merged infertility and non-infertility patient records
- Removed duplicate entries and cleaned missing values
- Detected and removed obvious outliers based on domain knowledge (e.g., implausible BP, hormone, and follicle values)
- Encoded categorical variables

### Exploratory Data Analysis (EDA)

- Examined:
  - Menstrual cycle length
  - Body Mass Index (BMI) patterns
  - Menstrual irregularity
  - Follicle numbers (left and right)
- Heatmaps used to identify highly correlated features
- Visualized correlations with PCOS using Seaborn and Matplotlib
- Concluded follicle count is a highly significant predictor of PCOS

### Modeling

- Random Forest Classifier
- Baseline model trained with default hyperparameters
- Performed hyperparameter tuning using GridSearchCV
  - Explored parameters such as:
    - n_estimators
    - max_depth
    - min_samples_split
    - min_samples_leaf
    - bootstrap
  - 5-fold cross-validation
- Achieved tuned accuracy of ~90% on test set
- Used a confusion matrix and classification report for evaluation

---

## Explainable AI (XAI)

Explainability was explored to help clinicians trust the machine learning pipeline. The SHAP (SHapley Additive exPlanations) library was considered to attribute model outputs to input features. Due to package conflicts, a full SHAP analysis was not completed, but the planned workflow included:

- Using SHAP TreeExplainer with the Random Forest model
- Generating SHAP summary plots (bar and beeswarm) to identify feature importance
- Providing model transparency, especially around the strong influence of follicle counts on PCOS diagnosis

This can be added in future work after environment dependencies are resolved.

---

## Results

- Baseline Random Forest accuracy: ~88%
- Tuned Random Forest accuracy: ~90%
- F1-score for PCOS class: ~0.84
- Highest correlated features: Follicle counts, LH, BMI
- The model showed strong generalization performance on unseen data

---

## Future Work

- Resolve SHAP visualization dependencies and integrate full model explainability
- Test additional XAI frameworks like LIME or counterfactuals
- Deploy the model with a simple Flask or Streamlit frontend for demonstration
- Expand to larger or multi-institution PCOS datasets

---

## How to Run

1. Clone the repository
2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
3.jupyter notebook pcos-diagnosis.ipynb
