# 🩺 Diabetes Prediction (Pima Indians Dataset)

🧠 **Goal:** Predict whether a patient has **diabetes (1)** or **no diabetes (0)** using clinical measurements, and compare 3 models: **Logistic Regression**, **Random Forest**, and **Gradient Boosting**.

📌 **Target:** `Outcome`  
- `1` = diabetes  
- `0` = no diabetes  

---

## 📊 Findings

✅ **Dataset**
- 768 records, 8 clinical features + 1 target
- No nulls in raw CSV, but multiple features contained **physiologically impossible zeros**

🧼 **Data cleaning (high impact)**
- Treated zero values as missing for:
  - `Glucose`, `BMI`, `SkinThickness`, `Insulin`, `BloodPressure`
- Replaced zeros with NaN and performed **Iterative Imputation** to recover realistic values:
  - Missing counts after zero→NaN:  
    - Insulin: 374  
    - SkinThickness: 227  
    - BloodPressure: 35  
    - BMI: 11  
    - Glucose: 5  
- Scaled features using **StandardScaler** before modeling

🧠 **Modeling approach**
- Train/test split: **80/20**, stratified
- Hyperparameter tuning using **GridSearchCV (5-fold CV)** with **recall** as the scoring metric (prioritizing detection of diabetic patients)

Models tuned:
- Logistic Regression: `C`  
- Random Forest: `n_estimators`, `max_depth`  
- Gradient Boosting: `n_estimators`, `learning_rate`

📈 **Model performance (test set)**
- Logistic Regression:  
  - Accuracy **0.7143** | Recall **0.5926** | Precision **0.5926** | F1 **0.5926**
- Random Forest:  
  - Accuracy **0.7273** | Recall **0.5556** | Precision **0.6250** | F1 **0.5882**
- Gradient Boosting (best overall F1):  
  - Accuracy **0.7273** | Recall **0.5926** | Precision **0.6154** | F1 **0.6038**

📌 **Conclusion**
- **Gradient Boosting** delivered the best balance (highest F1) while maintaining recall.
- Logistic Regression matched the best recall but with lower overall F1.

🔍 **Feature importance (consistent signal across models)**
Top drivers repeatedly identified:
- **Glucose** (strongest predictor across all models)
- **BMI**
- **Insulin**
Secondary contributors:
- DiabetesPedigreeFunction, Age, Pregnancies, SkinThickness, BloodPressure

🧩 **Deployment note**
- Attempted Streamlit UI integration; installation failed due to environment/network package resolution (pip could not locate Streamlit in that runtime).

---

## 👤 Author

Imanuel Annoh
