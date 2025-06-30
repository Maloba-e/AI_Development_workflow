# AI_Development_workflow
       ╔══════════════════════════════════════════════════════╗
       ║           HOSPITAL READMISSION PREDICTION            ║
       ║                 A Machine Learning Model              ║
       ╚══════════════════════════════════════════════════════╝

=================================================================
                        PROJECT OVERVIEW
=================================================================

This repository presents an AI model to predict hospital readmissions
within 30 days of discharge, developed as a group assignment to enhance
patient care and reduce hospital costs. The AI development workflow is a
structured process to design, build, train, evaluate, and deploy
artificial intelligence systems, ensuring accuracy, scalability, ethics,
and alignment with healthcare goals. The model leverages the
`hospital_readmissions.csv` dataset and employs a Random Forest Classifier
within a scikit-learn pipeline.

=================================================================
                        FEATURES
=================================================================

- Dataset: `hospital_readmissions.csv` with features like Age, Gender,
  Admission Type, Diagnosis, and Readmitted (target).
- Model: Random Forest Classifier integrated into a preprocessing and
  modeling pipeline.
- Preprocessing: Handles missing values, outliers, and categorical
  encoding.
- Evaluation: Reports accuracy, precision, recall, F1-score, and ROC-AUC.
- Output: Saves the trained model as `hospital_readmission_model.pkl`.

=================================================================
                        AI DEVELOPMENT WORKFLOW
=================================================================

The development of this AI model followed a structured workflow to ensure
a robust and effective solution:

a) Data Collection
   - Utilized `hospital_readmissions.csv` containing patient data such as
     Age, Gender, Admission Type, Diagnosis, and Readmitted status.
b) Data Processing
   - Filled missing `A1C_Result` values with 'Unknown'.
   - Capped `Age` outliers (>100) and imputed missing ages with the median.
   - Standardized categorical columns (Gender, Admission_Type, Diagnosis).
   - Converted `Readmitted` to binary (Yes=1, No=0).
   - Dropped non-predictive `Patient_ID`.
   - Scaled numeric features with StandardScaler and one-hot encoded
     categorical features with OneHotEncoder.
c) Model Selection
   - Chose Random Forest Classifier for its robustness and ability to
     handle mixed data types.
   - Considered Logistic Regression and XGBoost (not implemented).
d) Model Training
   - Split data into 80% training and 20% testing sets (stratified).
   - Trained the Random Forest model within a scikit-learn pipeline.
e) Model Evaluation
   - Computed metrics: accuracy, precision, recall, F1-score, ROC-AUC.
   - Performed 5-fold cross-validation with F1-score.
f) Model Deployment
   - Saved the trained model as `hospital_readmission_model.pkl` using
     joblib for future use.

=================================================================
                        REQUIREMENTS
=================================================================

- Python 3.x
- Libraries:
  * pandas
  * numpy
  * scikit-learn
  * joblib
Install dependencies:
    $ pip install pandas numpy scikit-learn joblib

=================================================================
                        INSTALLATION
=================================================================

1. Clone or download this repository.
2. Place `hospital_readmissions.csv` in the project directory.
3. Install required libraries (see above).

=================================================================
                        USAGE
=================================================================

1. Ensure `hospital_readmissions.csv` is in the working directory.
2. Run the main script (e.g., `main.py`):
    $ python main.py
3. The script will:
   - Load and preprocess the dataset.
   - Train the Random Forest model.
   - Evaluate and display performance metrics.
   - Save the model as `hospital_readmission_model.pkl`.

=================================================================
                        NOTES
=================================================================

- Performance Issue: The Random Forest model may show high accuracy but
  low precision/recall/F1-score, indicating potential class imbalance.
  Consider SMOTE or class weighting.
- Pipeline Gaps: Logistic Regression and XGBoost pipelines are referenced
  but not implemented. Define these for model comparison.
- Cross-Validation: Remove invalid `pos_label` in `cross_val_score` to
  avoid errors.

=================================================================
                    FUTURE IMPROVEMENTS
=================================================================

- Mitigate class imbalance using SMOTE or class weights.
- Implement and compare Logistic Regression and XGBoost pipelines.
- Optimize hyperparameters with GridSearchCV.
- Add visualizations (e.g., confusion matrix, ROC curve).
- Explore feature interactions or new derived features.

=================================================================
                        TROUBLESHOOTING
=================================================================

- Missing Dataset: Ensure `hospital_readmissions.csv` is present.
- Library Errors: Verify all required libraries are installed.
- Poor Metrics: Check class distribution with
  `df['Readmitted'].value_counts()` and apply balancing techniques.

