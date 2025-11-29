# Titanic Analysis 🚢

**End-to-End Machine Learning Classification Project**

A comprehensive data analysis and predictive modeling project on the Titanic dataset, demonstrating complete data science workflows from EDA to deployment-ready model.

## Project Overview

This project constructs a robust, end-to-end analytical pipeline that spans:
- **Data Collection & Preprocessing**: Handling missing values, feature engineering
- **Exploratory Data Analysis (EDA)**: Statistical summaries and visualizations
- **Machine Learning**: Logistic regression with 79% accuracy
- **Model Explainability**: SHAP values and feature importance analysis
- **Visualization**: Static (Matplotlib/Seaborn) and interactive plots (Plotly)

## Key Findings

- **Accuracy**: 79% (Precision: 75%, Recall: 68%, F1-Score: 71%)
- **Top Predictors**:
  - Gender (strong negative correlation: -0.54 with survival)
  - Passenger Class (socio-economic proxy)
  - Family Size (engineered feature)
  - Age & Fare

## Tech Stack

```
Python 3.x
- Data: pandas, NumPy
- ML: scikit-learn, XGBoost
- Visualization: Matplotlib, Seaborn, Plotly
- Interpretability: SHAP
```

## Model Performance

| Metric | Score |
|--------|-------|
| Accuracy | 0.788 |
| Precision | 0.773 |
| Recall | 0.689 |
| F1-Score | 0.729 |

## Key Insights

1. **Gender Effect**: 74% of females survived vs. 19% of males
2. **Class Disparity**: First-class passengers had significantly higher survival rates
3. **Age Factor**: Children and elderly had different survival patterns
4. **Fare Correlation**: Positive correlation (0.26) with survival

## Research Paper

Full research paper: "Data Analysis Using Python: A Comprehensive Study on the Titanic Dataset" by Ujaan Chatterjee

## License

MIT License

## Contact

- Email: itsujaanchatterjee@gmail.com
- LinkedIn: [Ujaan Chatterjee](https://www.linkedin.com/in/ujaan-chatterjee)
