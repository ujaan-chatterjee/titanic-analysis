# Titanic Analysis: Predictive Modeling & Survival Pattern Recognition 🚢

> **End-to-End Machine Learning Classification Project**
> 
> A production-grade data science project demonstrating advanced ML techniques on historical maritime disaster data, with comprehensive EDA, feature engineering, and interpretable predictive models achieving 78.8% accuracy.

---

## 📋 Quick Start

```bash
git clone https://github.com/ujaan-chatterjee/titanic-analysis.git
cd titanic-analysis
pip install -r requirements.txt
jupyter notebook
```

**Explore the analysis:**
- `01-eda.ipynb` - Exploratory Data Analysis with statistical insights
- `02-feature-engineering.ipynb` - Advanced feature extraction and transformation
- `03-model-training.ipynb` - Model selection, training, and hyperparameter tuning
- `04-model-evaluation.ipynb` - Cross-validation and performance analysis
- `05-explainability.ipynb` - SHAP values and feature importance interpretation

---

## 🎯 Project Overview

This project constructs a robust, production-ready analytical pipeline that spans:

- **Data Acquisition & Preprocessing** - Handling missing values using statistical imputation, outlier detection, and data validation
- **Exploratory Data Analysis (EDA)** - Statistical analysis, distribution profiling, correlation studies, and visualization-driven insights
- **Feature Engineering** - Creating derived features like family size, title extraction, and interaction terms
- **Machine Learning Pipeline** - Model selection, training, cross-validation, hyperparameter optimization
- **Model Explainability** - SHAP values, permutation importance, and decision boundary visualization  
- **Interactive Dashboards** - Plotly-based exploratory interfaces for stakeholder engagement
- **Documentation & Reproducibility** - Clean code, modular functions, and comprehensive comments

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| **Total Records** | 891 passengers |
| **Features** | 12 original + 5 engineered |
| **Target Variable** | Survival (Binary: Yes/No) |
| **Training Set** | 712 samples (80%) |
| **Test Set** | 179 samples (20%) |
| **Base Survival Rate** | 38.4% |

### Data Dictionary

- `PassengerId` - Unique identifier
- `Survived` - Survival status (0 = No, 1 = Yes) **[Target]**
- `Pclass` - Ticket class (1st, 2nd, 3rd)
- `Name` - Passenger name
- `Sex` - Gender (Male/Female)
- `Age` - Age in years
- `SibSp` - Number of siblings/spouses aboard
- `Parch` - Number of parents/children aboard
- `Ticket` - Ticket number
- `Fare` - Ticket price in GBP
- `Cabin` - Cabin number (highly sparse)
- `Embarked` - Port of embarkation (C=Cherbourg, Q=Queenstown, S=Southampton)

---

## 🔬 Methodology

### 1. Data Preprocessing

**Missing Value Strategy:**
- `Age`: Median imputation by passenger class (preserves distributional properties)
- `Embarked`: Mode imputation (majority port = Southampton)
- `Cabin`: Feature extraction (deck level) for subset of data

**Outlier Treatment:**
- Retained extreme fare values (reflects real wealth disparities)
- Flagged but preserved unusual age values

### 2. Feature Engineering

**Derived Features:**
- `FamilySize = SibSp + Parch + 1` (captures group dynamics)
- `IsAlone = 1 if FamilySize == 1` (isolation effect)
- `Title` (extracted from names: Mr., Mrs., Miss., Master, etc.)
- `Fare per person = Fare / FamilySize` (economic efficiency)
- `Age groups` (categorical: Child, Adult, Senior)

### 3. Exploratory Analysis

**Statistical Insights:**
- Descriptive statistics (mean, median, std, quartiles)
- Distribution analysis (histograms, KDE plots)
- Correlation matrices and heatmaps
- Contingency tables for categorical relationships
- Group-wise statistics (survival by class, gender, etc.)

### 4. Model Selection & Training

**Algorithms Evaluated:**
- Logistic Regression (interpretability baseline)
- Decision Trees (non-linear patterns)
- Random Forest (ensemble robustness)
- Gradient Boosting (sequential optimization)
- XGBoost (state-of-the-art performance)
- Support Vector Machines (non-linear classification)

**Hyperparameter Optimization:**
- Grid Search for parameter tuning
- Cross-validation (5-fold stratified)
- Learning curve analysis
- Validation set monitoring

---

## 🏆 Model Performance

### Logistic Regression (Final Model)

| Metric | Score | Interpretation |
|--------|-------|----------------|
| **Accuracy** | 0.788 | Correct predictions in 78.8% of cases |
| **Precision** | 0.773 | Of predicted survivors, 77.3% actually survived |
| **Recall** | 0.689 | Captured 68.9% of actual survivors |
| **F1-Score** | 0.729 | Balanced metric across precision/recall |
| **ROC-AUC** | 0.845 | Strong discrimination ability |

### Comparative Model Performance

```
Model                | Accuracy | ROC-AUC | Training Time
--------------------|----------|---------|---------------
Logistic Regression  | 0.788    | 0.845   | <100ms
Random Forest        | 0.826    | 0.882   | ~2s
XGBoost              | 0.834    | 0.892   | ~1s
Gradient Boosting    | 0.821    | 0.879   | ~3s
```

**Note:** Logistic Regression selected for production due to:
1. Excellent interpretability
2. Minimal computational overhead
3. Robust performance on holdout data
4. Easy to explain to non-technical stakeholders

---

## 🔍 Key Findings & Insights

### 1. **Gender Paradox: "Women and Children First"**
   - **Female survival rate:** 74% vs. **Male survival rate:** 19%
   - **Impact:** Strongest single predictor (correlation: -0.54)
   - **Historical context:** Maritime evacuation protocols prioritized women and children

### 2. **Class Hierarchy: Wealth as Proxy**
   - **1st Class:** 62% survival | **2nd Class:** 47% | **3rd Class:** 24%
   - **Mechanism:** 1st-class passengers closer to lifeboats, better informed
   - **Statistical significance:** Strong association with survival (p < 0.001)

### 3. **Age Demographics: Youth Advantage**
   - **Children (≤14 years):** 55% survival rate
   - **Young adults (15-35):** 35% survival
   - **Seniors (>60):** 27% survival
   - **Pattern:** Non-linear relationship with peak survival in young children

### 4. **Economic Disparity: Fare Premium Effect**
   - **Median fare - Survivors:** £29 vs. **Non-survivors:** £8
   - **Correlation:** Weak positive (0.26) but statistically significant
   - **Reason:** Fare correlates with class and cabin proximity

### 5. **Family Dynamics: Group Survival**
   - **Solo travelers:** 30% survival
   - **Families (2-4 members):** 48% survival
   - **Large groups (5+ members):** 11% survival
   - **Implication:** Group movement dynamics affected evacuation success

---

## 📊 Technical Stack

**Data & Analysis:**
- `pandas` - Data manipulation and cleaning
- `NumPy` - Numerical computations
- `scikit-learn` - ML algorithms and preprocessing
- `XGBoost` - Gradient boosting framework

**Visualization:**
- `Matplotlib` - Static plots and figures
- `Seaborn` - Statistical visualizations with style
- `Plotly` - Interactive dashboards and exploration

**Model Explainability:**
- `SHAP` - Shapley Additive exPlanations
- `lime` - Local Interpretable Model-Agnostic Explanations

**Development:**
- `Jupyter Notebook` - Interactive development and documentation
- `Python 3.8+` - Programming language

---

## 📁 Project Structure

```
titanic-analysis/
├── README.md                          # Project documentation
├── requirements.txt                   # Package dependencies
├── data/
│   ├── titanic.csv                    # Raw dataset
│   └── data_dictionary.md             # Data column descriptions
├── notebooks/
│   ├── 01-eda.ipynb                   # Exploratory Data Analysis
│   ├── 02-feature-engineering.ipynb   # Feature transformation
│   ├── 03-model-training.ipynb        # Model development
│   ├── 04-model-evaluation.ipynb      # Performance metrics
│   └── 05-explainability.ipynb        # SHAP & interpretability
├── src/
│   ├── preprocessing.py               # Data cleaning functions
│   ├── feature_engineering.py         # Feature creation
│   ├── model_utils.py                 # Training utilities
│   └── visualization.py               # Plotting functions
├── output/
│   ├── figures/                       # Static visualizations
│   └── reports/                       # Analysis summaries
└── LICENSE                            # MIT License
```

---

## 🚀 Advanced Features

### ✅ Model Explainability
- SHAP waterfall plots showing feature contributions
- Partial dependence plots for non-linear relationships
- Feature interaction detection and visualization

### ✅ Cross-Validation Strategy
- Stratified K-Fold (preserves class distribution)
- Time-series aware splitting (if temporal data)
- Custom CV for imbalanced datasets

### ✅ Hyperparameter Tuning
- Grid Search with exhaustive search
- Randomized Search for high-dimensional spaces
- Bayesian Optimization for efficient exploration

### ✅ Class Imbalance Handling
- SMOTE (Synthetic Minority Oversampling)
- Class weight adjustment
- Threshold optimization based on business requirements

---

## 📈 Key Metrics & Interpretation

| Metric | Definition | Use Case |
|--------|-----------|----------|
| **Accuracy** | (TP + TN) / All | Overall correctness |
| **Precision** | TP / (TP + FP) | False positive cost high |
| **Recall** | TP / (TP + FN) | False negative cost high |
| **F1-Score** | 2 × (Precision × Recall) / (Precision + Recall) | Balanced evaluation |
| **ROC-AUC** | Area Under the Curve | Model discrimination ability |
| **Log Loss** | Average cross-entropy | Probability calibration |

---

## 🔗 Related Research & References

### Inspirations
- Titanic historical research papers
- Maritime disaster analysis literature
- ML classification benchmarking studies

### Full Research Document
📄 **[Data Analysis Using Python: A Comprehensive Study on the Titanic Dataset](https://github.com/ujaan-chatterjee/titanic-analysis/blob/main/reports/research-paper.pdf)** - Detailed academic paper with methodology, literature review, and extended results

---

## 💡 Key Learnings & Best Practices

✅ **Data Quality:** Comprehensive preprocessing is 80% of ML success  
✅ **Feature Engineering:** Domain knowledge + statistical analysis = better features  
✅ **Model Selection:** No free lunch theorem - test multiple approaches  
✅ **Explainability:** Black-box models are untrustworthy in production  
✅ **Validation:** Always reserve holdout test data for final evaluation  
✅ **Documentation:** Future you will thank present you  

---

## 🔮 Future Enhancements

- [ ] Deep Learning model (Neural Networks for non-linear patterns)
- [ ] Ensemble stacking combining multiple model predictions
- [ ] Production deployment with FastAPI/Flask REST endpoint
- [ ] Real-time prediction dashboard with Streamlit
- [ ] Model monitoring and drift detection
- [ ] A/B testing framework for model updates
- [ ] Privacy-preserving differential privacy implementation
- [ ] Transfer learning from similar classification tasks

---

## 📝 Reproducibility & Citation

**How to Reproduce:**
```bash
# Install dependencies
pip install -r requirements.txt

# Run all notebooks in sequence
jupyter notebook

# Execute complete pipeline
python run_pipeline.py
```

**Citation:**
```bibtex
@project{chatterjee2024titanic,
  title={Titanic Analysis: Predictive Modeling \& Survival Pattern Recognition},
  author={Chatterjee, Ujaan},
  year={2024},
  url={https://github.com/ujaan-chatterjee/titanic-analysis}
}
```

---

## 📧 Contact & Connect

**Questions, feedback, or collaboration inquiries?**

- **Email:** [itsujaanchatterjee@gmail.com](mailto:itsujaanchatterjee@gmail.com)
- **LinkedIn:** [Ujaan Chatterjee](https://www.linkedin.com/in/ujaan-chatterjee)
- **GitHub:** [ujaan-chatterjee](https://github.com/ujaan-chatterjee)
- **Portfolio:** [Complete Projects](https://github.com/ujaan-chatterjee?tab=repositories)

---

## ⚖️ License

MIT License - Feel free to use this project for educational and commercial purposes.

See [LICENSE](LICENSE) for full details.

---

**Last Updated:** November 2024  
**Status:** Active & Maintained ✅
