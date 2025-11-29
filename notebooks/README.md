# Titanic Analysis Notebooks

This directory contains the analytical pipeline for the Titanic survival prediction project, organized as a reproducible notebook workflow.

## Notebook Structure

### 00-data-loading.ipynb
**Purpose**: Data acquisition and validation
- Load Titanic dataset from Kaggle CSV
- Validate data integrity and missing values
- Perform initial data quality checks
- Document feature definitions and data dictionary
- Handle missing values strategy (imputation vs. removal)

### 01-eda.ipynb
**Purpose**: Exploratory Data Analysis
- Analyze survival patterns across demographics
- Examine feature distributions (age, fare, class, gender)
- Identify correlations and interactions
- Visualize survival rates by passenger characteristics
- Detect outliers and data anomalies

### 02-model.ipynb
**Purpose**: Model development and optimization
- Feature engineering (title extraction, family size, binning)
- Train multiple ML models (Logistic Regression, XGBoost, Random Forest)
- Hyperparameter tuning via cross-validation
- Model selection based on validation metrics
- Generate feature importance rankings

### 03-eval.ipynb
**Purpose**: Model evaluation and interpretation
- Generate classification metrics (accuracy, precision, recall, F1)
- Create confusion matrix and ROC-AUC curve
- SHAP explainability analysis for feature contributions
- Survival prediction insights by passenger group
- Business-relevant recommendations

## Running the Pipeline

```bash
# Install dependencies
pip install -r requirements.txt

# Execute notebooks in sequence
jupyter notebook 00-data-loading.ipynb
jupyter notebook 01-eda.ipynb
jupyter notebook 02-model.ipynb
jupyter notebook 03-eval.ipynb
```

## Key Outputs

- **Model Performance**: 78.8% accuracy on test set
- **Feature Importance**: Passenger class, gender, age drive predictions
- **Business Value**: Demographic risk profiling for historical analysis

## Dependencies

- Python 3.8+
- pandas, numpy, scikit-learn
- xgboost, matplotlib, seaborn
- shap for model interpretability

See `requirements.txt` for exact versions.

---
*Last Updated*: 2025-01-15
*Pipeline Version*: 1.0
