# 23CSE301 Machine Learning - Capstone Project (Review 1)

**Academic Year:** 2026-27  
**Degree:** B.Tech. (Computer Science and Engineering) - III Year  
**Team Members:** Balamurugan, Mitranad, Deepak Surya  

---

## 📋 Overview

This repository contains the deliverables for **Review 1** of the Machine Learning Capstone Project. The project implements end-to-end Machine Learning pipelines for two problem tracks:
1. **Regression Track:** 10 Regression Algorithms trained on the Building Energy Efficiency dataset.
2. **Classification Track (Part A):** 5 Classification Algorithms trained on the Healthcare Stroke Prediction dataset.

---

## 📁 Repository Layout

```text
Review 1 ML capstone/
├── data/
│   ├── energy_efficiency.xlsx             # Regression Track Dataset
│   └── healthcare-dataset-stroke-data.csv # Classification Track Dataset
├── notebooks/
│   ├── regression.ipynb                   # Full Regression Track Pipeline (10 Algorithms + EDA + Preprocessing + Tuning + Plots)
│   └── classification.ipynb               # Classification Track Part A Pipeline (5 Classifiers + EDA + Preprocessing + Confusion Matrices)
├── models/
│   ├── best_regression_model.pkl          # Saved Binary Model (Gradient Boosting Regressor)
│   └── best_classification_model.pkl      # Saved Binary Model (Random Forest Classifier)
├── README.md                              # Project documentation
└── requirements.txt                       # Python dependencies
```

---

## 📊 Datasets Summary

### 1. Regression Track Dataset
* **Dataset:** Building Energy Efficiency Dataset (`data/energy_efficiency.xlsx`)
* **Samples:** 768 building shape configurations
* **Features:** 8 architectural inputs ($X_1 \dots X_8$: Relative Compactness, Surface Area, Wall Area, Roof Area, Overall Height, Orientation, Glazing Area, Glazing Area Distribution)
* **Target Variable ($Y_1$):** `Heating_Load` ($\text{kWh/m}^2$)

### 2. Classification Track Dataset
* **Dataset:** Healthcare Stroke Prediction Dataset (`data/healthcare-dataset-stroke-data.csv`)
* **Samples:** 5,110 patient records
* **Features:** 11 clinical & demographic attributes (age, glucose level, BMI, hypertension, heart disease, work type, smoking status, etc.)
* **Target Variable:** `stroke` (Binary: `0` = No Stroke, `1` = Stroke)

---

## 🔍 Outlier Detection & Data Preprocessing Summary

| Dataset | Attribute | Outliers Identified ($1.5 \times \text{IQR}$) | Handling Strategy & Rationale |
| :--- | :--- | :--- | :--- |
| **Energy Efficiency (Regression)** | All features ($X_1 \dots X_8$) & Target ($Y_1$) | **0 Outliers** | Controlled Ecotect architectural software simulation sweep across bounded building parameter grids. Data is clean and uniform. |
| **Stroke Prediction (Classification)** | `avg_glucose_level` | **627 Outliers** ($> 169.35\text{ mg/dL}$) | **Retained (Clinical Signal):** High blood glucose ($>200\text{ mg/dL}$) and severe obesity ($BMI > 45$) are direct medical risk factors for stroke. Dropping them would remove critical stroke patient signals. Handled using `StandardScaler`. |
| | `bmi` | **110 Outliers** ($> 47.5\text{ kg/m}^2$) | Missing values (~3.9%) imputed using median fitted strictly on `X_train`. Outliers retained. |
| | `age` | **0 Outliers** | Balanced distribution across age groups. |

---

## 🚀 Environment Setup & Execution

1. **Install required dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

3. **Execute Notebooks:** Open `notebooks/regression.ipynb` and `notebooks/classification.ipynb` and run all cells top-to-bottom.
