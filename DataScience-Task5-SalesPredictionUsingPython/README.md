# Sales Prediction Using Advertising Budget

A machine learning project that predicts sales from advertising spend on TV, Radio and Newspaper, and finds which channel matters most. Built as a task of the Oasis Infobyte Data Science internship (OIBSIP).

## Objective
Build and compare regression models that predict sales from advertising budgets, check that the results hold up with cross-validation, and identify which advertising channel has the greatest impact.

## Dataset
"Advertising Budget and Sales" (`Advertising Budget and Sales.csv`).

| Detail | Value |
|---|---|
| Markets | 200 |
| Features | TV, Radio and Newspaper advertising budgets (thousands of dollars) |
| Target | Sales (millions of dollars) |
| Missing values | None |
| Duplicate rows | None |
| Outliers | 2 high Newspaper budgets (kept, because they are real values) |

The original file has an extra unnamed index column, which was dropped.

## Approach
1. **Load and prepare the data:** dropped the index column and renamed the columns.
2. **Exploratory analysis:** data checks, outlier box plots, a pairplot, scatter plots of sales against each channel, and a correlation heatmap.
3. **Train/test split:** 80% training (160 markets) and 20% testing (40 markets).
4. **Models:** Linear Regression as a baseline, and a Random Forest Regressor (100 trees) as a more flexible model.
5. **Evaluation:** MAE, RMSE and R² on the test set.
6. **Cross-validation:** 5-fold cross-validation on all 200 markets to check the results were not due to one lucky split.
7. **Residual analysis:** residual plots for both models.
8. **Feature importance:** Random Forest importance, permutation importance, and a test of removing Newspaper from the model.
9. **Prediction:** used both models on a new budget.

## Results

**On the test set (40 markets)**

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 1.4608 | 1.7816 | 0.8994 |
| Random Forest | 0.6201 | 0.7686 | 0.9813 |

**5-fold cross-validation (all 200 markets)**

| Model | R² (mean) | R² (std) | MAE | RMSE |
|---|---|---|---|---|
| Linear Regression | 0.8827 | 0.0395 | 1.2873 | 1.7057 |
| Random Forest | 0.9805 | 0.0050 | 0.5431 | 0.7079 |

MAE and RMSE are in millions of dollars of sales revenue.

**Which channel matters most**

| Channel | Correlation with Sales | Random Forest importance | Linear Regression coefficient |
|---|---|---|---|
| TV | 0.78 | 62.5% | 0.0447 |
| Radio | 0.58 | 36.2% | 0.1892 |
| Newspaper | 0.23 | 1.3% | 0.0028 |

## Key Findings
- **Random Forest is clearly the better model.** It has a higher R² (0.98 against 0.88 in cross-validation) and about half the average error (0.54 against 1.29 million dollars), and the result holds across all 5 folds.
- **Linear Regression misses a curve in the data.** Its residual plot shows a curved pattern, meaning the link between spend and sales is not perfectly straight. Random Forest's residuals are scattered around zero with no pattern.
- **TV is the main driver of sales,** then Radio. Both importance methods give the same ranking.
- **Radio has the largest effect per dollar spent,** while TV drives most of the overall predictions.
- **Newspaper adds almost nothing.** Removing it from the Linear Regression model did not lower its cross-validated score (0.8827 with it, 0.8844 without).

## Example Prediction
For a budget of 150 thousand dollars on TV, 25 thousand on Radio and 10 thousand on Newspaper, Linear Regression predicts about 14.45 million dollars in sales and Random Forest predicts about 15.22 million dollars.

## How to Run
1. Clone this repository or download the folder.
2. Install the libraries:
   ```
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
3. Keep `Advertising Budget and Sales.csv` in the same folder as the notebook. In the loading cell, use `pd.read_csv('Advertising Budget and Sales.csv')` (the notebook may use a Google Colab path starting with `/content/`).
4. Open `DataScience-Task5-SalesPrediction.ipynb` in Jupyter Notebook or Google Colab and run all cells from top to bottom.

## Project Structure
```
DataScience-Task5-SalesPrediction/
├── DataScience-Task5-SalesPrediction.ipynb   # Full analysis and models
├── Advertising Budget and Sales.csv          # Dataset
└── README.md                                 # Project description
```

## Limitations
- The data is observational (200 markets), so the results show associations, not proof that changing a budget will change sales.
- Predictions are only reliable inside the budget ranges in the data (for example, Radio up to about 50 thousand dollars).
- The Random Forest was not tuned, and the dataset is small.
- The size of the effects (for example, about 189,000 dollars of sales per 1,000 dollars of Radio spend) is very large compared with real-world returns, so use the results to compare channels against each other, not as exact forecasts of return on investment.

## Tech Stack
Python, pandas, scikit-learn, matplotlib, seaborn, Jupyter Notebook

## Author
**Hanifah Morayo Abdulazeez**
LinkedIn: www.linkedin.com/in/hanifahmorayoabdulazeez

Completed as part of the Oasis Infobyte Data Science Internship (#oasisinfobyte).
