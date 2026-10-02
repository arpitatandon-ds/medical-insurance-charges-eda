# Medical Insurance Charges: EDA & Preprocessing

Exploratory data analysis, data cleaning, feature engineering, and feature selection on a medical insurance dataset. The goal is to understand which personal and lifestyle factors drive individual medical `charges`, and to prepare a clean feature set for regression modelling.

> 🚧 **Status:** EDA and preprocessing are complete. Train/test split and regression models are the next step.

## Dataset

- **Source:** [Medical Cost Personal Datasets (Kaggle)](https://www.kaggle.com/datasets/mirichoi0218/insurance)
- **Size:** 1,338 rows and 7 columns (1,337 rows after removing 1 duplicate)

| Column | Description |
|---|---|
| `age` | Age of the primary beneficiary |
| `sex` | Female / male |
| `bmi` | Body mass index |
| `children` | Number of dependents covered |
| `smoker` | Smoker / non-smoker |
| `region` | Residential region in the US (northeast, northwest, southeast, southwest) |
| `charges` | Medical costs billed by insurance (target variable) |

## What's Inside

1. **Exploratory Data Analysis**
   - Shape, data types, summary statistics, missing values
   - Distributions of numeric and categorical features
   - Boxplots for spread and outliers
   - Correlation heatmap
2. **Data Cleaning & Preprocessing**
   - Removed duplicate rows
   - Encoded `sex` and `smoker` as binary columns (`is_female`, `is_smoker`)
   - One-hot encoded `region`
3. **Feature Engineering**
   - Created BMI categories: Underweight, Normal, Overweight, Obese
4. **Feature Selection**
   - Pearson correlation of each feature with `charges`
   - Chi-square test of independence for categorical features (against quartile-binned `charges`, α = 0.05)

## Key Findings

- **Smoking is the strongest driver of charges**, with a Pearson correlation of about 0.79.
- **Age** has a moderate positive relationship with charges (about 0.30).
- **BMI** has a weaker overall relationship with charges, but being in the **Obese** category carries more signal than the other BMI categories.
- Most region and BMI-category dummies did not pass the chi-square test at α = 0.05.

## Project Structure

```
medical-insurance-charges-eda/
├── data/
│   └── insurance.csv
├── notebooks/
│   └── insurance_charges_eda_preprocessing.ipynb
├── requirements.txt
└── README.md
```

## Getting Started

```bash
git clone https://github.com/<your-username>/medical-insurance-charges-eda.git
cd medical-insurance-charges-eda
pip install -r requirements.txt
jupyter notebook notebooks/insurance_charges_eda_preprocessing.ipynb
```

**requirements.txt**

```
numpy
pandas
matplotlib
seaborn
scipy
jupyter
```

## Tech Stack

Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy

## Next Steps

- [ ] Train/test split
- [ ] Feature scaling (fit on the training set only, to avoid data leakage)
- [ ] Train and compare regression models (Linear Regression, Random Forest, Gradient Boosting)
- [ ] Evaluate with R², MAE, and RMSE
- [ ] Try a log transform on the skewed `charges` target
- [ ] Add interaction features (e.g. smoker × BMI)

## Author

**Arpita**
[LinkedIn](https://www.linkedin.com/in/arpita-tandon-31b3b7267) · [GitHub](https://github.com/arpitatandon-ds)
