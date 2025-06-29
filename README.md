# PCOScope

A machine learning pipeline to diagnose Polycystic Ovary Syndrome (PCOS) and explore infertility patterns using clinical and ultrasound data, supported by explainable AI techniques.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Technical Approach](#technical-approach)
  - [Data Preprocessing](#data-preprocessing)
  - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
  - [Model Building](#model-building)
  - [Explainable AI](#explainable-ai)
- [Results](#results)
- [Requirements](#requirements)
- [How to Run](#how-to-run)
- [Future Scope](#future-scope)
- [License](#license)

---

## Project Overview

PCOScope is an end-to-end data science workflow to detect PCOS and analyze related infertility factors in women. It uses a Random Forest classifier with hyperparameter tuning, and includes explainable AI (SHAP) to identify the most influential features affecting PCOS prediction.

---

## Technical Approach

### Data Preprocessing

- Merged two datasets: one with PCOS patients and one without infertility
- Handled missing values
- Dropped irrelevant columns
- Removed outliers based on clinical domain knowledge
- Encoded categorical features
- Ensured consistent datatypes

### Exploratory Data Analysis (EDA)

- Correlation heatmaps to select relevant features
- Visualization of patterns in:
  - menstrual cycle length
  - BMI distributions
  - follicle counts
  - lifestyle attributes
- Distribution plots for feature understanding

### Model Building

- Features (`X`) and target (`y`) assigned
- Training and test splits (70-30)
- Baseline Random Forest classifier
- GridSearchCV for hyperparameter tuning
- Final best Random Forest trained on optimal hyperparameters
- Evaluation via accuracy, confusion matrix, classification report

### Explainable AI

- SHAP (SHapley Additive exPlanations) was integrated to explain Random Forest predictions
- Identified that *follicle number (both left and right)* had the highest predictive contribution
- Visualized feature importances using summary plots

---

## Results

- Final tuned Random Forest achieved ~90% accuracy on test data
- Confusion matrix showed strong sensitivity and specificity for PCOS diagnosis
- SHAP interpretability highlighted follicle counts as the most crucial predictor, aligning with clinical findings

---

## Requirements

All dependencies are specified in `requirements.txt`.

Install them with:

```bash
pip install -r requirements.txt
```

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/PCOScope.git
   ```
2. Navigate into the project folder:
   ```bash
   cd PCOScope
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Launch the Jupyter Notebook to run the pipeline:
   ```bash
   jupyter notebook
   ```
   and open `pcos-diagnosis.ipynb`.

---

## Future Scope

- Add cross-validation on multiple ML algorithms (XGBoost, LightGBM)
- Incorporate additional clinical variables
- Extend interpretability using LIME or advanced SHAP visualizations
- Deploy as a simple web app for demonstration

---

