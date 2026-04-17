# Comparison of Traditional and Quantum Approaches in Educational Analytics

**Major Project — B.Tech CSE (Data Science)**  
Visakha Institute of Engineering and Technology

A hybrid quantum-classical machine learning pipeline that compares traditional ML algorithms against a Quantum Variational Circuit (VQC) for predicting student placement outcomes in educational analytics.

---

## Overview

This project investigates whether quantum machine learning can outperform classical approaches on a real-world educational dataset. Five classical models and one quantum model (VQC using Qiskit) were trained, evaluated, and compared on student placement prediction.

---

## Dataset

| Property | Details |
|----------|---------|
| Records | 506 students |
| Features | 11 (CGPA, internships, projects, attendance, backlogs, branch, gender, etc.) |
| Target | Placement Status (Placed / Not Placed) |
| Source | College placement dataset |

**Features used:** `college_id`, `student_name`, `gender`, `academic_year`, `branch`, `overall_cgpa`, `internships`, `placement_status`, `projects`, `crt_classes`, `attendance`, `backlogs`

---

## Models Compared

### Classical Models
| Model | Accuracy | Precision | Recall | F1 Score |
|-------|----------|-----------|--------|----------|
| Random Forest (RF) | 97.82% | 96.95% | 98.08% | 97.44% |
| XGBoost | 99.41% | 99.59% | 99.00% | 99.27% |
| SVM | 82.02% | 80.54% | 86.27% | 80.84% |
| Logistic Regression | 89.53% | 86.86% | 90.23% | 88.05% |
| MLP Neural Network | 88.53% | 88.42% | 83.47% | 85.25% |
| XGBoost (Tuned) | **100.00%** | **100.00%** | **100.00%** | **100.00%** |

### Quantum Model
| Model | Accuracy | Precision | Recall | F1 Score |
|-------|----------|-----------|--------|----------|
| VQC (Qiskit) | 53.92% | 24.24% | 26.67% | 25.40% |

---

## Key Findings

- **XGBoost (tuned)** achieved perfect classification (100% accuracy, F1, ROC-AUC) on the test set
- **Random Forest** performed strongly with 97.82% accuracy — best among untuned classical models
- **Quantum VQC** achieved only 53.92% accuracy, marginally better than random guessing
- Current quantum hardware/simulators are limited by qubit count and noise — classical models outperform quantum on small tabular datasets
- Quantum ML shows theoretical promise but is not yet practical for structured educational data at this scale

---

## Tech Stack

| Category | Tools |
|----------|-------|
| Language | Python |
| Classical ML | Scikit-learn, XGBoost |
| Quantum ML | Qiskit, Qiskit Machine Learning |
| Quantum Circuit | ZZFeatureMap + RealAmplitudes (VQC) |
| Optimizer | COBYLA (maxiter=50) |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib |
| Model Saving | Joblib |
| Environment | Google Colab |

---

## Pipeline Architecture

```
Raw CSV Data
     ↓
Data Cleaning + Target Encoding
     ↓
ColumnTransformer (Numerical: Impute + Scale | Categorical: Impute + OneHotEncode)
     ↓
SelectKBest Feature Selection
     ↓
┌─────────────────────┬──────────────────────┐
│   Classical Models  │    Quantum Model      │
│  RF, XGB, SVM,      │  VQC (ZZFeatureMap   │
│  LR, MLP            │  + RealAmplitudes)    │
└─────────────────────┴──────────────────────┘
     ↓
5-Fold Stratified Cross Validation
     ↓
GridSearchCV (XGBoost Hyperparameter Tuning)
     ↓
Evaluation: Accuracy, Precision, Recall, F1, ROC-AUC
```

---

## How to Run

1. Clone this repository
2. Install dependencies:
```bash
pip install qiskit qiskit-aer qiskit-machine-learning scikit-learn xgboost joblib matplotlib pandas numpy
```
3. Open the `.ipynb` file in Google Colab
4. Upload `500_records.csv` when prompted
5. Run all cells in order

---

## Research Paper

A research paper documenting the methodology, experiments, and findings is included in this repository (`research_paper.pdf`).

---

## Skills Demonstrated

`Python` `Quantum Machine Learning` `Qiskit` `VQC` `XGBoost` `Random Forest` `SVM` `Logistic Regression` `MLP` `Scikit-learn` `GridSearchCV` `Cross Validation` `Feature Engineering` `Pipeline Architecture` `Educational Analytics` `Research`

---

## Author

**Vommi Lahari**  
B.Tech CSE (Data Science) — Visakha Institute of Engineering and Technology  
[LinkedIn](https://linkedin.com/in/lahari-vommi-9b3173346) | [GitHub](https://github.com/vommilahari28)
