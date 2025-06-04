# Aircraft Hub Inspection Predictive Modeling

![Python](https://img.shields.io/badge/Python-3.8+-blue) ![Machine Learning](https://img.shields.io/badge/ML-Classification-orange) ![Industry](https://img.shields.io/badge/Industry-Aviation-green) ![Power BI](https://img.shields.io/badge/PowerBI-F2C811?style=flat&logo=powerbi&logoColor=black)

**Predictive modeling for aircraft wheel hub crack detection using machine learning**

*NDT Engineering to Data Science career transition project - An introductory machine learning project*

## Project Overview

Machine learning application for predicting crack occurrences in aircraft wheel hubs using eddy current testing (ET) data. This project demonstrates end-to-end data science capabilities in a safety-critical aviation environment.

**Key Achievement: 82% Recall in crack detection using Weighted XGBoost**

## Business Problem

Aircraft wheel hub inspections are critical for aviation safety. Missing a crack (False Negative) could lead to catastrophic failure, while false alarms (False Positives) result in unnecessary maintenance costs. This project prioritizes **maximizing recall** to ensure no cracks are missed.

### Dataset Characteristics
- 8,870 total inspection records across multiple hub types
- Focused on 385 Type 05 Main Wheel records (highest crack rate: 18.24%)
- Class distribution: 86% No Crack vs 14% Crack
- 5.6 years of operational data

## Technical Approach

### Data Pipeline
1. **Data Collection**: Manual digitization from inspection logbooks
2. **Data Cleaning**: 74% missing value imputation success rate
3. **Feature Engineering**: One-hot encoding, scaling, temporal features
4. **Model Training**: Progressive complexity from Logistic Regression to XGBoost

### Model Performance Comparison

| Model | Precision | Recall | F1 | ROC AUC | Approach |
|-------|-----------|--------|----|---------|----------|
| Logistic Regression | 0.00 | 0.00 | 0.00 | 0.51 | Baseline |
| Random Forest | 0.19 | 0.45 | 0.26 | 0.62 | class_weight='balanced' |
| RF + SMOTE | 0.25 | 0.27 | 0.26 | 0.63 | Synthetic oversampling |
| **XGBoost Weighted** | **0.21** | **0.82** | **0.33** | **0.66** | **scale_pos_weight optimization** |

## Key Insights

### Feature Importance (SHAP Analysis)
1. **Hub Cycle**: Most critical predictor - higher usage cycles increase crack probability
2. **Total Inspections**: Inspector experience/workload correlation
3. **Part Number Variations**: Specific part designs show different failure rates
4. **Inspector Groups**: Performance consistency across teams

### Business Intelligence
- **Survivor Bias**: Inspection volume drops after Cycle 4 as cracked hubs are removed
- **Part Reliability**: PN007 shows 23% crack rate vs PN008 at 5.3%
- **Temporal Patterns**: Seasonal variations in detection rates
- **Maintenance Strategy**: Data-driven cycle-based scheduling recommendations

## Visualizations

**Power BI Dashboards:**
- Hub type analysis and crack rate comparison
- Inspector performance and workload distribution
- Temporal trend analysis
- Part number reliability assessment

**Model Analysis:**
- Confusion matrices across all approaches
- SHAP feature importance and impact analysis
- Model performance comparison charts

## Technologies

- **ML Framework**: Scikit-learn, XGBoost, Imbalanced-learn
- **Analysis**: Pandas, NumPy, SciPy
- **Visualization**: Power BI, Matplotlib, Seaborn
- **Interpretability**: SHAP

## Results

**Model Performance:**
- 82% recall in crack detection (9 out of 11 cracks identified)
- Acceptable precision trade-off for safety-critical application
- Clear feature importance ranking for operational insights

**Business Impact:**
- Predictive maintenance capability for high-risk components
- Resource optimization through targeted inspection strategies
- Enhanced safety through reduced undetected crack probability

## Project Structure

```
├── notebooks/          # Analysis and modeling notebooks
├── visualizations/     # Power BI dashboards and plots
├── docs/               # Methodology and documentation
└── README.md           # Project overview
```

---

**About:** This project bridges NDT engineering expertise with modern machine learning techniques, demonstrating practical data science application in aviation safety. The focus on interpretability and recall optimization reflects real-world constraints in safety-critical industries.
