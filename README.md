# AAI-530 Final Project – Group 2  
## Predictive Maintenance for Industrial IoT Systems  
Shiley-Marcos School of Engineering – University of San Diego  
Master of Applied Artificial Intelligence

---

## Team Members
- Dina Othman  
- Saman Tavasoli  
- Matt Hashemi  

---

# Project Overview

This project develops predictive maintenance models using an Industrial IoT dataset containing sensor readings and machine operating conditions.

The objectives of this project are to:

- Predict **machine failure risk (classification)**
- Forecast **future torque values (time-series regression)**
- Compare **traditional machine learning models** with **deep learning models (MLP & LSTM)**

The notebooks follow a clear modeling pipeline:

> **EDA → Traditional Machine Learning → Time-Series Forecasting → Deep Learning**

---

# Notebook Structure & Execution Flow

Please run the notebooks in the following order:

---

## 1- eda_preprocessing.ipynb

### Purpose
- Data cleaning  
- Exploratory Data Analysis (EDA)  
- Feature engineering  
- Time proxy justification (Tool wear [min])  
- Removal of leakage features  
- Final modeling dataset preparation  

### Output
- Cleaned dataset ready for modeling  

This notebook prepares the dataset used by all subsequent models.

---

## 2- model1A_classification_machine_failure.ipynb  
### Traditional Machine Learning – Failure Classification

### Objective
Predict binary machine failure.

### Models Implemented
- Logistic Regression  
- Random Forest  
- Gradient Boosting  

### Key Components
- Time-aware feature engineering (lags + rolling statistics)
- Time-ordered train/test split (no data leakage)
- ROC-AUC, PR-AUC, confusion matrices
- Feature importance analysis
- Tableau-ready prediction export

This notebook provides interpretable failure risk modeling using traditional ML methods.

---

## 3- model1B_regression_torque_forecast.ipynb  
### Traditional Machine Learning – Time-Series Regression

### Objective
Predict next-step torque (`Torque_future`).

### Models Implemented
- Linear Regression  
- Ridge Regression  
- Random Forest Regressor  

### Key Components
- One-step-ahead forecasting
- Time-ordered split
- RMSE, MAE, R² evaluation
- Tableau-ready prediction export

This notebook fulfills the **required time-series prediction model (traditional ML)** for the course.

---

## 4- model2_deep_learning.ipynb  
### Deep Learning – MLP & LSTM

### Objective
Predict machine failure using neural networks.

### Models Implemented
- Feedforward Neural Network (MLP)
- LSTM (sequence-based modeling)

### Key Components
- Sequence generation using tool wear as time proxy
- Train/validation/test split
- Class weighting for imbalance handling
- ROC & PR curves
- Training history visualization
- Saved model artifacts
- Tableau-ready prediction export

This notebook fulfills the **required deep learning model built from scratch** for the course.

---

# Modeling Summary

| Notebook | Model Type | Target | Purpose |
|-----------|------------|--------|----------|
| Model1A | Traditional ML (Classification) | Machine Failure | Risk prediction |
| Model1B | Traditional ML (Regression) | Future Torque | Time-series forecasting |
| Model2 | Deep Learning (MLP + LSTM) | Machine Failure | Sequence modeling |

---

# Outputs

Each modeling notebook generates:

- Evaluation metrics
- Plots (ROC curves, PR curves, confusion matrices, training curves)
- CSV exports for dashboard visualization

Generated outputs are stored in the `/outputs` directory.

---

# Tableau Dashboard – Deployment Evaluation

To simulate a realistic Industrial IoT deployment workflow, exported prediction files were visualized using **Tableau Public**.

The dashboard provides an operational comparison of:

- Traditional ML vs LSTM performance
- Deployment-style accuracy evaluation
- Predicted failure counts
- Risk probability trends over degradation progression

### Deployment Context

Unlike internal notebook validation, the Tableau dashboard evaluates:

- Exported prediction probabilities
- Fixed classification threshold (0.5)
- Sequential operational behavior

This reflects how the models would behave in a simulated production environment.

### Deployment Accuracy

- Traditional Model: **22.16%**
- LSTM Model: **56.89%**

(Note: These deployment metrics differ from internal validation results due to thresholding and class imbalance (~3.39% failure rate).)

### Tableau Public Link

https://public.tableau.com/app/profile/saman.tavasoli/viz/LSTM_vs_Traditional_Predictive_Maintenance/Dashboard14

---

# Important Notes

- All train/test splits are **time-ordered** to prevent data leakage.
- Tool wear is used as a **time proxy** since the dataset does not contain timestamps.
- Aggregation was used to construct temporal sequences.
- Results should be interpreted within the limitations of the dataset structure.

---

## Full Project PDF

For convenience, all notebooks (including outputs, visualizations, and results) have been compiled into a single document:

**AAI530-Group2-Final-Project-Predictive-Maintenance-Full-Version.pdf**

This PDF provides a complete, sequential view of the entire project and is the recommended file for grading.

---

# Setup Instructions

**Prerequisites:** Python 3.11.7

### 1. Create a virtual environment
   ```bash
   python3.11 -m venv env
   ```

### 2. Activate the environment on macOS/Linux
   ```bash
   source env/bin/activate
   ```

### 3. Install the dependencies
   ```bash
   pip install -r requirements.txt
   ```

### 4. To deactivate the virtual environment, run:
   ```bash
   deactivate
   ```
