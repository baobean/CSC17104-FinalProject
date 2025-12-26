# CSC17104-FinalProject

## Project Overview

This project analyzes the **CDC Diabetes Health Indicators** dataset to understand risk factors, patterns, and predictive models for diabetes. Using statistical analysis and machine learning techniques, we investigate how lifestyle factors, health conditions, demographics, and their interactions influence diabetes prevalence.

The analysis is divided into six research questions spanning feature importance analysis, interaction effects, demographic patterns, stratified analysis, predictive modeling, and prevalence threshold identification.

## Team Information

- **Course:** CSC17104 - Programming for Data Science
- **Team:** Group 03
- **Project:** Final Project - Diabetes Health Indicators Analysis

## Dataset

### Source
- **Name:** CDC Diabetes Health Indicators
- **Origin:** CDC's Behavioral Risk Factor Surveillance System (BRFSS) 2015
- **Cleaned Version:** Processed by Alex Teboul
- **UCI ML Repository ID:** 891
- **Links:**
  - [UCI ML Repository](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators)
  - [Kaggle Dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)
- **License:** CC0: Public Domain (freely usable)

### Description
- **Size:** 253,680 rows × 22 columns (after removing duplicates)
- **Data Type:** Survey responses from telephone interviews of U.S. adults (one per household)
- **Target Variable:** `Diabetes_binary` (0 = no diabetes, 1 = prediabetes or diabetes)
- **Features:** 21 health-related and demographic variables including:
  - **Health Conditions:** `HighBP`, `HighChol`, `Stroke`, `HeartDiseaseorAttack`
  - **Lifestyle Factors:** `Smoker`, `PhysActivity`, `Fruits`, `Veggies`, `HvyAlcoholConsump`
  - **Physical Metrics:** `BMI`, `PhysHlth` (days with poor physical health), `MentHlth` (days with poor mental health)
  - **Healthcare Access:** `CholCheck`, `AnyHealthcare`, `NoDocbcCost`
  - **Demographics:** `Age`, `Sex`, `Education`, `Income`
  - **Other:** `GenHlth` (general health rating), `DiffWalk` (difficulty walking)

## Research Questions

1. Which features (among lifestyle factors, health conditions, and demographic variables) are most important for predicting diabetes risk?

2. How do lifestyle factors (smoking, physical activity) and health conditions (high BP, high cholesterol) interact to affect diabetes prevalence? Are combined effects more significant than individual factors?

3. How is Body Mass Index (BMI) associated with diabetes prevalence, and does this relationship vary across demographic groups?

4. How do socioeconomic factors (particularly income level) modify the relationship between lifestyle factors and diabetes risk?

5. Can we build a predictive model to identify individuals at high risk of diabetes based on their lifestyle factors, health behaviors, and existing health conditions?

6. How does diabetes prevalence vary across different demographic groups and health behavior categories, and what are the critical threshold values where diabetes risk increases substantially?

## Key Findings Summary

1. **BMI is the strongest modifiable predictor** of diabetes risk, with importance scores of 0.183 in Random Forest
2. **Cardiovascular conditions show synergistic effects:** Having both HighBP and HighChol creates 29.7% diabetes risk vs. 22.9% expected from addition alone
3. **Physical activity is highly protective:** Reduces diabetes risk by 37-50% even among smokers and high-risk groups
4. **Random Forest model achieves ROC-AUC of 0.806**, demonstrating feasibility of ML-based diabetes risk prediction
5. **Socioeconomic disparities exist:** Lower income and education levels show higher diabetes prevalence even after controlling for lifestyle factors
6. **Age and obesity interact:** BMI-diabetes relationship strengthens significantly in older populations
7. **Critical risk thresholds:** BMI ≥ 30, Age ≥ 50, Income < $25,000 mark escalation points

## File Structure

The project is organized into multiple Jupyter notebooks, each focusing on specific research questions:

- **`Group03.ipynb`** - Main notebook containing:
  - Dataset loading and initial exploration
  - Data cleaning (duplicate removal)
  - Column inventory and data type verification
  - Numerical feature analysis
  
- **`Group03-Q1,2.ipynb`** - Analysis for Questions 1 and 2:
  - **Question 1:** Feature importance analysis using Logistic Regression, Decision Tree, Random Forest
  - **Question 2:** Interaction effects of Smoker × PhysActivity and HighBP × HighChol with chi-square and ANOVA tests
  
- **`Group03-Q3,4.ipynb`** - Analysis for Questions 3 and 4:
  - **Question 3:** BMI-diabetes association stratified by demographics (Age, Sex, Income, Education)
  - **Question 4:** Stratified analysis focusing on income-level effect modification
  
- **`Group03-Q5,6.ipynb`** - Analysis for Questions 5 and 6:
  - **Question 5:** Predictive modeling with model comparison and performance evaluation
  - **Question 6:** Prevalence patterns across demographics and behaviors with comprehensive ANOVA analysis

## How to Run

### Prerequisites
Ensure you have Python 3.8+ installed with the following packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy statsmodels ucimlrepo
```

### Execution Order

1. **Start with the main notebook:**
   ```
   Group03.ipynb
   ```
   This notebook loads the dataset and performs initial exploration. Run all cells to:
   - Fetch the dataset from UCI ML Repository
   - Remove duplicates
   - Verify data integrity

2. **Run question-specific notebooks** (order flexible):
   - `Group03-Q1,2.ipynb` - Feature importance and interaction analysis
   - `Group03-Q3,4.ipynb` - BMI-demographics and stratified analysis
   - `Group03-Q5,6.ipynb` - Predictive modeling and prevalence patterns

3. **Each notebook is self-contained** and can be run independently as they all fetch/load the dataset at the beginning.

### Note on Data Loading
The notebooks use `ucimlrepo` package to fetch data directly:
```python
from ucimlrepo import fetch_ucirepo
cdc_diabetes_health_indicators = fetch_ucirepo(id=891).data.original
```

No manual dataset download is required.

## Dependencies

### Required Python Packages

| Package | Purpose | Installation |
|---------|---------|--------------|
| `pandas` | Data manipulation and analysis | `pip install pandas` |
| `numpy` | Numerical computations | `pip install numpy` |
| `matplotlib` | Data visualization | `pip install matplotlib` |
| `seaborn` | Statistical data visualization | `pip install seaborn` |
| `scikit-learn` | Machine learning models and evaluation | `pip install scikit-learn` |
| `scipy` | Statistical tests (chi-square, t-tests, ANOVA) | `pip install scipy` |
| `statsmodels` | Advanced statistical analysis and ANOVA | `pip install statsmodels` |
| `ucimlrepo` | UCI ML Repository dataset fetching | `pip install ucimlrepo` |

### Install All Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy statsmodels ucimlrepo
```

Or using requirements file:
```bash
pip install -r requirements.txt
```

### Environment
- **Python Version:** 3.8 or higher
- **Development Environment:** Jupyter Notebook or JupyterLab
- **Operating System:** Platform-independent (Windows, macOS, Linux)