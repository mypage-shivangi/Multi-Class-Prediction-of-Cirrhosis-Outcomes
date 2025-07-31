## 🩺 Cirrhosis Outcomes Prediction – Multi-Class Classification

This notebook builds a machine learning model to **predict the final status of patients with liver cirrhosis** based on their clinical features. The outcome can be:

- **C**: Censored (patient still alive)  
- **D**: Death  
- **L**: Liver Transplant  

We treat this as a **multi-class classification** problem.

---

## 📌 Problem Statement

**Goal:** Predict the final patient outcome (`Status`) given features like bilirubin, albumin, ascites, prothrombin time, etc.

**Target Variable:**  
- `Status`:  
  - **C** → Censored  
  - **D** → Death  
  - **L** → Liver Transplant  

**Dataset Source:** [Kaggle - Cirrhosis Dataset](https://www.kaggle.com/datasets/itachi9604/disease-symptom-description-dataset)

---

## 🧼 Data Preprocessing

- **Dropped Columns**:
  - `ID`, `Drug`, `Sex` (where not useful or redundant)

- **Imputation**:
  - Numerical features: imputed using **median**
  - Categorical features: imputed using **mode**

- **Encoding**:
  - Converted `Status` to numerical: `C = 0`, `D = 1`, `L = 2`
  - Applied `LabelEncoder` to features like `Stage`, `Ascites`, `Spiders`

- **Scaling**:
  - Applied `MinMaxScaler` to numerical features for uniformity

---

## 🧪 Feature Engineering

- Derived feature interactions were minimal to maintain medical interpretability  
- Categorical values were label-encoded rather than one-hot encoded to preserve model simplicity

---

## 🧠 Model Training & Evaluation

Evaluated multiple models:

| Model             | Accuracy | F1 Score (Macro) | Notes                                    |
|------------------|----------|------------------|------------------------------------------|
| Logistic Regression | ~70%   | ~0.68            | Baseline model                           |
| Random Forest     | ~74%     | ~0.72            | Handled non-linearities well             |
| ✅ XGBoost (Final) | ~76%     | ~0.74            | Best performing model after tuning       |

- **Final Model:** ✅ **XGBoostClassifier**  
- **Cross-validation:** Stratified K-Fold  
- **Evaluation Metrics**:
  - Accuracy  
  - F1 Score (Macro)  
  - Confusion Matrix  

---

## 📁 Files

- [`multi-class-prediction-of-cirrhosis-outcomes.ipynb`](https://www.kaggle.com/code/shivangi2k18/multi-class-prediction-of-cirrhosis-outcomes) – Main notebook  
- `data/` – Contains training data file (CSV)  
- `submission.csv` – Final predictions in required format  

---

## 🏁 Final Results

- **Best Model:** ✅ XGBoostClassifier  
- **Accuracy:** ~76%  
- **Macro F1 Score:** ~0.74  
- Improved interpretability while preserving predictive power

---

## 🚀 Future Work

- Add SHAP interpretability for medical insights  
- Explore deep learning (e.g. TabNet or DNN with attention)  
- Evaluate time-series disease progression (if longitudinal data available)

---

## 📬 Contact

Connect with me on [LinkedIn](https://www.linkedin.com/in/shivangigupta01) if you’d like to collaborate or discuss the project!
