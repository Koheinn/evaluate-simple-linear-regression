# Evaluate Simple Linear Regression

## 📌 Project Overview

This project is part of **Course 4 of the Google Advanced Data Analytics Professional Certificate**.

The objective of this activity was to perform a complete **simple linear regression analysis** to investigate the relationship between marketing promotional budgets and sales. The analysis focuses on identifying which marketing channel has the strongest linear relationship with sales and evaluating whether a simple linear regression model is appropriate for predicting sales.

The analysis includes:

* Exploratory Data Analysis (EDA)
* Data quality and missing-value analysis
* Visualization of relationships between variables
* Selection of an independent variable for regression
* Ordinary Least Squares (OLS) regression
* Evaluation of linear regression assumptions
* Model performance evaluation
* Interpretation of coefficients
* Statistical significance and confidence intervals
* Business recommendations

The dataset contains fictional marketing campaign data covering **TV, Radio, and Social Media promotional budgets**, along with the resulting sales generated from each promotion.

---

## 🎯 Objectives

The main objectives of this project were to:

1. Explore the marketing and sales dataset.
2. Understand the distributions and characteristics of the variables.
3. Identify the marketing variable with the strongest linear relationship with sales.
4. Build and fit a simple linear regression model.
5. Check the four major assumptions of linear regression:

   * Linearity
   * Independence
   * Normality
   * Homoscedasticity
6. Evaluate model performance using statistical measures.
7. Interpret regression coefficients.
8. Evaluate coefficient uncertainty using p-values and confidence intervals.
9. Translate statistical findings into business recommendations.

---

## 📂 Repository Structure

```text
evaluate-simple-linear-regression/
│
├── Evaluate simple linear regression.ipynb
├── marketing_and_sales_data_evaluate_lr.csv
└── README.md
```

### Files

| File                                       | Description                                                                                                                |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| `Evaluate simple linear regression.ipynb`  | Jupyter Notebook containing the complete analysis, visualizations, regression model, assumption checks, and interpretation |
| `marketing_and_sales_data_evaluate_lr.csv` | Dataset containing marketing promotional budgets and sales                                                                 |
| `README.md`                                | Project documentation and summary of findings                                                                              |

---

## 📊 Dataset

The dataset contains information about marketing promotions across three channels:

* **TV** — TV promotional budget, in millions of dollars
* **Radio** — Radio promotional budget, in millions of dollars
* **Social_Media** — Social media promotional budget, in millions of dollars
* **Sales** — Sales generated from the promotion, in millions of dollars

Each row represents an independent marketing promotion.

The dataset contains:

* **4,572 rows**
* **4 columns**

## The analysis found a small amount of missing data in the `Sales` variable. Approximately **0.13%** of the rows had missing sales values, so those rows were removed before modeling.

## 🛠️ Technologies & Libraries

The analysis was performed using Python and the following libraries:

* **Python**
* **Pandas** — data manipulation and analysis
* **Matplotlib** — data visualization
* **Seaborn** — statistical visualization
* **Statsmodels** — statistical modeling and OLS regression
* **Jupyter Notebook** — interactive analysis environment

### Imports

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

import statsmodels.api as sm
from statsmodels.formula.api import ols
```

---

# 🔎 Exploratory Data Analysis

## Dataset Dimensions

The dataset initially contained:

```text
Rows:    4,572
Columns: 4
```

The independent variables were:

* `TV`
* `Radio`
* `Social_Media`

The dependent variable was:

* `Sales`

---

## Descriptive Statistics

The descriptive statistics showed the following ranges:

| Variable     |  Mean | Minimum | Maximum |
| ------------ | ----: | ------: | ------: |
| TV           | 54.07 |   10.00 |  100.00 |
| Radio        | 18.16 |  0.0007 |   48.87 |
| Social Media |  3.32 | 0.00003 |   13.98 |

These values represent promotional budgets in millions of dollars.

---

## Sales Distribution

A histogram was used to examine the distribution of sales.

The analysis found that sales were generally distributed between approximately **$25 million and $350 million** across the promotions.

---

# 📈 Selecting the Predictor Variable

A Seaborn pairplot was used to visually compare relationships between the variables.

The analysis showed that:

* **TV and Sales** had the strongest linear relationship.
* **Radio and Sales** also showed a linear relationship, but with greater variation.
* **Social Media and Sales** showed a weaker relationship.

Therefore, **TV** was selected as the independent variable `X` for the simple linear regression model.

---

# 🧮 Simple Linear Regression Model

The model was created using **Ordinary Least Squares (OLS)** regression.

The regression formula was:

```text
Sales ~ TV
```

The resulting regression equation was:

```text
Sales = -0.1263 + 3.5614 × TV
```

where:

* `Sales` is measured in millions of dollars.
* `TV` is the TV promotional budget in millions of dollars.
* `-0.1263` is the intercept.
* `3.5614` is the estimated slope for TV.

---

# 📊 Model Results

The fitted model produced the following key statistics:

| Metric                     |              Value |
| -------------------------- | -----------------: |
| R-squared                  |          **0.999** |
| Adjusted R-squared         |          **0.999** |
| F-statistic                |    **4.527 × 10⁶** |
| Number of observations     |          **4,556** |
| TV coefficient             |         **3.5614** |
| TV p-value                 |          **0.000** |
| TV 95% Confidence Interval | **[3.558, 3.565]** |
| Intercept                  |        **-0.1263** |
| Intercept p-value          |          **0.209** |

The regression output showed an R-squared of **0.999**, meaning that approximately **99.9% of the variation in Sales is explained by TV promotional spending in this simple regression model**.

---

# 🧪 Regression Assumption Checks

Before interpreting a linear regression model, its assumptions should be evaluated.

Four major assumptions were considered:

1. Linearity
2. Independence
3. Normality
4. Homoscedasticity

These checks were explicitly performed in the notebook.

---

## 1. Linearity

A scatterplot of `TV` versus `Sales` was created.

### Result

The visualization showed a clear linear relationship between TV promotional spending and sales.

**Conclusion:** The linearity assumption was considered satisfied.

---

## 2. Independence

Each row represents an independent marketing promotion.

Therefore, the observations were treated as independent of one another.

**Conclusion:** The independence assumption was considered satisfied.

---

## 3. Normality of Residuals

Residuals were calculated from the fitted model.

Two visualizations were used:

* Histogram of residuals
* Normal Q-Q plot

The residual histogram was approximately normally distributed, and the Q-Q plot showed the residuals following a relatively straight line.

**Conclusion:** The normality assumption was considered satisfied.

---

## 4. Homoscedasticity

A scatterplot of fitted values versus residuals was created to evaluate whether residual variance remained approximately constant.

The residual variance appeared consistent across the range of fitted values.

**Conclusion:** The homoscedasticity assumption was considered satisfied.

---

# 📐 Coefficient Interpretation

The estimated TV coefficient was:

```text
3.5614
```

This means that, according to this model, a **$1 million increase in the TV promotional budget is associated with an estimated $3.5614 million increase in sales**.

The fitted relationship is:

```text
Sales = -0.1263 + 3.5614 × TV
```

The TV coefficient was highly statistically significant, with:

```text
p-value = 0.000
```

and a 95% confidence interval of:

```text
[3.558, 3.565]
```

These results indicate a very precise estimate of the TV coefficient within the fitted model.

---

# 📏 Model Confidence

The model's R-squared value was:

```text
R² = 0.999
```

This indicates that the TV variable explains approximately **99.9% of the observed variation in Sales** within this dataset and model.

The TV coefficient also had a very small p-value and a narrow 95% confidence interval, indicating relatively little statistical uncertainty around the estimated slope.

---

# 💼 Business Insights

The analysis provides several important business insights.

### 1. TV was the strongest predictor

Among the three available promotional channels:

```text
TV
Radio
Social Media
```

TV showed the strongest positive linear relationship with sales.

### 2. Strong relationship between TV spending and sales

The simple linear regression model produced:

```text
R² = 0.999
```

Therefore, TV promotional spending was an extremely strong predictor of sales within this dataset.

### 3. Estimated effect of TV spending

The model estimates that:

> A $1 million increase in TV promotional spending corresponds to an estimated $3.5614 million increase in sales.

### 4. Statistical confidence

The TV coefficient had:

```text
p-value = 0.000
95% CI = [3.558, 3.565]
```

This provides strong statistical evidence for the positive relationship between TV promotional spending and sales within the model.

---

# 🧠 Key Takeaways

This project provided practical experience with the complete simple linear regression workflow.

### Data Analysis

* Performed exploratory data analysis.
* Examined dataset dimensions and descriptive statistics.
* Identified and handled missing values.
* Visualized distributions and relationships between variables.

### Statistical Modeling

* Selected an appropriate predictor using exploratory visualization.
* Built an OLS regression model using `statsmodels`.
* Interpreted regression coefficients.
* Evaluated model fit using R-squared.

### Model Diagnostics

* Checked linearity.
* Considered independence.
* Evaluated residual normality.
* Evaluated homoscedasticity.

### Statistical Interpretation

* Interpreted regression coefficients.
* Used p-values to evaluate statistical significance.
* Used confidence intervals to assess coefficient uncertainty.

These are important components of a professional regression analysis workflow.

---

# 🚀 Possible Next Steps

Although the activity focused on simple linear regression using TV as the only predictor, several extensions could be explored.

### Multiple Linear Regression

Instead of using only TV, a multiple regression model could include:

```text
Sales ~ TV + Radio + Social_Media
```

This would allow the combined contribution of the three marketing channels to be investigated.

### Model Comparison

Different regression models could be compared to determine whether adding additional marketing variables improves predictive performance.

### Prediction

The fitted model could be used to estimate expected sales for different TV promotional budgets.

### Visualization

A regression line could be added to the TV-versus-Sales scatterplot using Seaborn's `regplot()` to make the relationship easier to communicate to stakeholders.

---

# 📌 Final Recommendation

Based on the analysis, **TV promotional spending should be prioritized over Radio and Social Media if the goal is to increase sales**, because TV demonstrated the strongest positive linear relationship with Sales in the dataset.

The model estimates an additional **$3.5614 million in sales for every additional $1 million invested in TV promotion**, under the assumptions of this fitted model.

> **Important:** This result describes the relationship observed in the provided dataset and should not automatically be interpreted as proof that increasing TV spending causally produces the stated increase in sales. Further analysis, including multiple regression and potentially causal methods, would be useful before making real-world budget allocation decisions.

---

# 🧰 How to Run the Project

## 1. Clone the repository

```bash
git clone <your-repository-url>
cd evaluate-simple-linear-regression
```

## 2. Install the required libraries

```bash
pip install pandas matplotlib seaborn statsmodels jupyter
```

Alternatively, if you use Anaconda:

```bash
conda install pandas matplotlib seaborn statsmodels jupyter
```

## 3. Start Jupyter Notebook

```bash
jupyter notebook
```

## 4. Open the notebook

Open:

```text
Evaluate simple linear regression.ipynb
```

Make sure the CSV file is located in the same directory as the notebook:

```text
marketing_and_sales_data_evaluate_lr.csv
```

## 5. Run the notebook

Run the cells from top to bottom to reproduce the exploratory analysis, visualizations, regression model, diagnostics, and results.

---

# 📚 Course

**Google Advanced Data Analytics Professional Certificate**

**Course 4 — Regression Analysis: Simplify Complex Data Relationships**

This project demonstrates practical application of regression analysis concepts using Python.

---

# 📖 References

* Saragih, H. S. (2020). *Dummy Marketing and Sales Data*. Kaggle.
* Matplotlib documentation — `axline()`
* Seaborn documentation — `pairplot()`, `scatterplot()`, and `histplot()`
* Statsmodels documentation — OLS regression and Q-Q plots

The original activity also references the fictional marketing and sales dataset and supporting Python documentation.

---

# 👨‍💻 Author

**Heinn Htet Zan**

Aspiring Data Scientist / Machine Learning Engineer with a background in full-stack software development and an interest in **Data Science, Machine Learning, Artificial Intelligence, and Analytics**.

---

## ⭐ Project Highlights

```text
Dataset                → Marketing & Sales
Observations           → 4,572 initially
Model observations     → 4,556
Regression type        → Simple Linear Regression
Method                 → Ordinary Least Squares (OLS)
Predictor              → TV
Target                 → Sales
R²                     → 0.999
TV coefficient         → 3.5614
TV p-value              → 0.000
95% CI                  → [3.558, 3.565]
```

**Main finding:** TV promotional spending demonstrated an exceptionally strong positive linear relationship with sales in this dataset.
