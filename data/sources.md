# Dataset Sources & References

## Primary Dataset

### Titanic Dataset (RMS Titanic Passenger Data)

**Source**: Kaggle - Titanic: Machine Learning from Disaster
- **URL**: https://www.kaggle.com/c/titanic/data
- **License**: Public domain / Educational use
- **Access**: Available through Kaggle Competitions platform

**Dataset Specifications**:
- **Format**: CSV (Comma-Separated Values)
- **Training Set**: 891 records with 12 features
- **Test Set**: 418 records (target variable excluded)
- **Total Features**: 12 original features + 5 engineered features
- **Target Variable**: Survived (Binary: 0/No, 1/Yes)

---

## Feature Dictionary

| Feature | Type | Description | Missing % |
|---------|------|-------------|----------|
| PassengerId | Integer | Unique identifier for each passenger | 0% |
| Survived | Binary | Survival outcome (target) | 0% |
| Pclass | Categorical (1-3) | Ticket class (1=Upper, 2=Middle, 3=Lower) | 0% |
| Name | String | Passenger full name | 0% |
| Sex | Categorical | Gender (male/female) | 0% |
| Age | Float | Age in years | 19.9% |
| SibSp | Integer | # of siblings/spouses aboard | 0% |
| Parch | Integer | # of parents/children aboard | 0% |
| Ticket | String | Ticket number | 0% |
| Fare | Float | Ticket price in GBP | 0.1% |
| Cabin | String | Cabin location | 77.1% |
| Embarked | Categorical | Port of embarkation (C/Q/S) | 0.2% |

---

## Data Quality Notes

### Missing Values
- **Age**: 177 missing values (19.9%) - Imputed using median by passenger class
- **Embarked**: 2 missing values (0.2%) - Imputed using mode (Southampton)
- **Cabin**: 687 missing values (77.1%) - Feature extracted (deck level) where available
- **Fare**: 1 missing value (0.1%) - Imputed using median fare

### Outliers & Anomalies
- **Fare distribution**: Highly right-skewed with extreme values (£0 - £512)
- **Age extremes**: Preserved as authentic (includes infants and elderly)
- **Parch/SibSp**: Valid values range 0-8 (no obvious errors)

### Data Imbalance
- **Survived=0 (Did not survive)**: 549 samples (61.6%)
- **Survived=1 (Survived)**: 342 samples (38.4%)
- **Imbalance ratio**: 1.60:1 (addressed through stratified sampling)

---

## Data Acquisition Process

1. **Download**: Dataset obtained from Kaggle platform
2. **Initial Load**: CSV files imported using pandas
3. **Validation**: Schema verification and type inference
4. **Preprocessing**: See `notebooks/00-data-loading.ipynb` for detailed steps
5. **Storage**: Raw data preserved in `data/raw/` directory

---

## Related Resources

### Historical Context
- [Titanic Historical Society](https://www.titanichistoricalsociety.org/)
- [NTSB Titanic Accident Report](https://en.wikipedia.org/wiki/Sinking_of_the_Titanic)
- [Wreck Discovery & Research](https://www.bbc.com/bitesize/guides/zj4yn39/revision/1)

### Similar Datasets
- Lusitania sinking survival data
- Halifax Explosion survivor records
- General maritime disaster datasets

---

## Reproducibility

To reproduce this analysis:
1. Download dataset from Kaggle
2. Place CSV files in `data/raw/` directory
3. Run `notebooks/00-data-loading.ipynb` for preprocessing
4. Follow sequential notebooks 01-03 for complete pipeline

**Last Updated**: November 2024  
**Data Version**: v1.0  
**MD5 Checksum**: (for validation purposes)
