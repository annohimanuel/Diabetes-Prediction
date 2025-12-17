# Project Requirements: Diabetes Prediction (Pima Indians Dataset)

## Objective
Build and compare machine learning models to predict whether a patient has diabetes using clinical and demographic predictors. The project must include data cleaning for physiologically impossible values, model selection focused on recall, and feature-importance analysis to support interpretability.

## Inputs and Output
### Inputs (Features)
- Pregnancies
- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI
- DiabetesPedigreeFunction
- Age

### Output (Target)
- Outcome (0 = no diabetes, 1 = diabetes)

## Key Questions to Answer
### Healthcare / Business Questions
- Can we identify diabetic patients early with acceptable accuracy while minimizing missed cases?
- Which model best supports early detection when prioritizing recall?
- Which clinical factors most strongly drive diabetes predictions?

### Analytical Questions
- Which features contain invalid “zero” values that must be treated as missing?
- What imputation approach best restores realistic values?
- How do Logistic Regression, Random Forest, and Gradient Boosting compare under the same evaluation framework?

## Required Workflow Deliverables
1. **Data ingestion**
   - Load `diabetes.csv`, verify schema, shape, and dtypes

2. **Data quality checks**
   - Validate missingness (null checks)
   - Identify physiologically impossible zero values

3. **Data cleaning**
   - Replace zeros with NaN for:
     - Glucose, BMI, SkinThickness, Insulin, BloodPressure
   - Impute missing values using **IterativeImputer**
   - Confirm no remaining missing values

4. **Preprocessing**
   - Separate features (X) and target (y)
   - Standardize features with **StandardScaler**
   - Split into train/test sets (80/20) with stratification

5. **Model training + tuning**
   - Train 3 models:
     - Logistic Regression
     - Random Forest
     - Gradient Boosting
   - Tune hyperparameters with **GridSearchCV (5-fold)**
   - Use **recall** as the optimization metric

6. **Evaluation**
   - Compute:
     - Accuracy, Recall, Precision, F1-score
   - Visualize:
     - Confusion matrix for each model
   - Compare models in a single metrics table

7. **Interpretability**
   - Logistic Regression: coefficients as importance
   - Random Forest / Gradient Boosting: feature_importances_
   - Rank and visualize top predictors

## Success Criteria
- Clean handling of invalid zeros and reproducible preprocessing
- Model comparison reported with consistent metrics
- Prioritization of recall for clinical screening use case
- Clear feature importance results highlighting primary drivers (e.g., Glucose/BMI/Insulin)
