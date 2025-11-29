# Titanic Survival Analysis - Executive Summary

**Report Date**: January 15, 2025  
**Analysis Period**: Historical (RMS Titanic Disaster, April 1912)  
**Dataset**: Kaggle Titanic Passenger Manifest  
**Status**: Complete Analysis ✓

## Executive Overview

This project analyzes survival patterns from the Titanic disaster using machine learning classification techniques. The dataset contains 891 passenger records with 12 features including demographic, travel class, and fare information. Our models achieve **78.8% accuracy** in predicting survival outcomes.

## Key Findings

### Overall Survival Rate
- **38.4%** of passengers survived (342 out of 891)
- **61.6%** of passengers did not survive (549 out of 891)
- Significant disparity based on passenger demographics

### Critical Survival Factors

#### 1. **Gender** (Strongest Predictor)
- Female passengers: **~73% survival rate**
- Male passengers: **~19% survival rate**
- Evidence of "women and children first" evacuation protocol

#### 2. **Passenger Class** (High Impact)
- First Class: **~62% survival** (Upper deck priority)
- Second Class: **~47% survival** (Middle deck)
- Third Class: **~24% survival** (Lower deck, overcrowded)

#### 3. **Age** (Moderate Correlation)
- Children (<10 years): Higher survival probability
- Adults (20-40 years): Variable by gender
- Elderly (60+): Lower survival rates

#### 4. **Fare Paid** (Socioeconomic Indicator)
- Positive correlation with survival
- Higher fares indicate 1st/2nd class access
- Premium passengers prioritized in evacuation

## Model Performance

### Classification Metrics
- **Accuracy**: 78.8%
- **Precision**: 0.76 (Survived class)
- **Recall**: 0.65 (Missed some survivors)
- **F1-Score**: 0.70
- **ROC-AUC**: 0.84

### Best Performing Model
**Random Forest Classifier** with 100 estimators
- Captures non-linear relationships
- Feature importance ranking available
- Robust to class imbalance

### Feature Importance Ranking
1. Passenger Class (Pclass) - 28%
2. Gender (Sex) - 26%
3. Fare - 18%
4. Age - 15%
5. Family Size - 13%

## Technical Specifications

### Data Processing
- Missing Values:
  - Age: 177 entries (19.9%) - Imputed with median
  - Cabin: 687 entries (77.1%) - Excluded from analysis
  - Embarked: 2 entries (0.2%) - Imputed with mode
- Feature Engineering:
  - Title extraction from passenger names
  - Family size calculation (SibSp + Parch + 1)
  - Age binning for non-linear patterns
  - Categorical encoding for Sex and Embarked port

### Training Configuration
- Train/Test Split: 80/20
- Cross-Validation: 5-fold
- Scaling: StandardScaler (mean=0, std=1)
- Random State: 42 (reproducibility)

## Business Insights

### Demographic Risk Profiling
- **Highest Risk**: 3rd class males (19% survival)
- **Moderate Risk**: 2nd class (47% survival)
- **Lowest Risk**: 1st class females (95% survival)
- **Special Case**: Children prioritized regardless of class

### Historical Context
- Evacuation followed social/class hierarchy
- Limited lifeboat capacity (1,178 vs. 2,224 aboard)
- Crew prioritization influenced survival
- Communication failures impacted lower deck passengers

## Recommendations

### For Maritime Safety Standards
1. **Equal Access Protocol**: Ensure lifeboats reach all passenger decks
2. **Clear Communication**: Multilingual emergency procedures
3. **Training Requirements**: Crew evacuation expertise
4. **Capacity Planning**: Lifeboats ≥ total passenger capacity

### For Future Analysis
1. Incorporate crew survival data
2. Analyze port of embarkation effects
3. Time-based survival curves
4. SHAP explainability for individual predictions

## Project Deliverables

- ✓ Data Loading & Validation (00-data-loading.ipynb)
- ✓ Exploratory Data Analysis (01-eda.ipynb)
- ✓ Model Development (02-model.ipynb)
- ✓ Evaluation & Insights (03-eval.ipynb)
- ✓ Feature Dictionary (data/sources.md)
- ✓ Development Roadmap (ROADMAP.md)

## Data Source

**Kaggle Titanic Dataset**  
https://www.kaggle.com/c/titanic/data

- Training Set: 891 passengers
- Test Set: 418 passengers
- Features: PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked

---

**Next Steps**: Deploy model for inference on unlabeled test set. Integrate SHAP analysis for stakeholder communication.

*Report compiled by Ujaan Chatterjee*  
*Last Updated: 2025-01-15*
