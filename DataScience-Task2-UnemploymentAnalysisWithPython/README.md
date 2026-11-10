# Unemployment Analysis in India (2020)

An exploratory data analysis of unemployment across Indian states, with a focus on the impact of the COVID-19 lockdown. Built as Task 2 of the Oasis Infobyte Data Science internship (OIBSIP).

## Objective
Explore regional and monthly unemployment trends in India during 2020, and measure how the COVID-19 pandemic changed unemployment, employment and labour participation.

## Dataset
"Unemployment in India" from Kaggle (`Unemployment_Rate_upto_11_2020.csv`).

| Detail | Value |
|---|---|
| Rows | 267 (one per state per month) |
| States | 27, grouped into 5 zones (North, South, East, West, Northeast) |
| Period | 31 January 2020 to 31 October 2020 |
| Missing values | None |
| Duplicate records | None |

| Column | Meaning |
|---|---|
| State | Indian state |
| Date | Month-end date |
| Unemployment_Rate | Estimated unemployment rate (%) |
| Employed | Estimated number of people employed |
| Labour_Participation_Rate | Share of the working-age population employed or looking for work (%) |
| Region_Zone | Zone of India |

Note: January, February and April have 26 states instead of 27. The file name says "11_2020", but the last month in the data is October.

## Approach
1. **Load and clean:** renamed columns, removed extra spaces, converted dates, fixed swapped latitude/longitude names, and checked for missing values and duplicates.
2. **Region-wise averages:** average unemployment rate for each zone.
3. **Month-wise trend:** average unemployment rate for each month, with the lockdown start marked.
4. **Top 10 states:** states with the highest average unemployment rate.
5. **Time series:** monthly unemployment for Maharashtra, Delhi and Tamil Nadu.
6. **Correlation heatmap:** unemployment rate, number employed and labour participation rate.
7. **Pre-COVID vs post-COVID:** data split at 1 March 2020, plus a three-phase view (pre-COVID, lockdown, recovery).

## Results

**Average unemployment rate by zone**

| Zone | Average rate |
|---|---|
| North | 15.89% |
| East | 13.92% |
| Northeast | 10.95% |
| South | 10.45% |
| West | 8.24% |

**Highest average unemployment by state**

| State | Average rate |
|---|---|
| Haryana | 27.48% |
| Tripura | 25.06% |
| Jharkhand | 19.54% |
| Bihar | 19.47% |
| Delhi | 18.41% |

**Pre-COVID vs post-COVID**

| Measure | Pre-COVID (Jan-Feb) | Post-COVID (Mar-Oct) | Change |
|---|---|---|---|
| Unemployment rate | 9.23% | 12.96% | +3.73 points (+40%) |
| Employed (average per state) | 15.56 million | 13.57 million | -12.8% |
| Labour participation rate | 44.40% | 41.02% | -3.38 points |

**Three phases**

| Phase | Unemployment rate | Employed (average per state) | Labour participation |
|---|---|---|---|
| Pre-COVID (Jan-Feb) | 9.23% | 15.56 million | 44.40% |
| Lockdown (Mar-May) | 18.71% | 12.23 million | 39.62% |
| Recovery (Jun-Oct) | 9.56% | 14.37 million | 41.86% |

## Key Findings
- **The lockdown caused a sharp spike.** Average unemployment was about 9.2% in January and February, rose to 22.2% in April and peaked at 23.2% in May, then fell to 10.9% in June and 8.0% by October.
- **The rate recovered faster than jobs.** By the recovery phase unemployment was back near its pre-COVID level (9.56% against 9.23%), but employment and labour participation were still lower than before, so the job market had not fully recovered by October.
- **Some states were already high before the lockdown.** In January-February, Tripura averaged 30.5%, Haryana 23.1%, Jammu & Kashmir 20.9% and Delhi 18.5%. Tamil Nadu and Puducherry reached the top 10 mainly because of the lockdown shock.
- **State trajectories differed.** Tamil Nadu peaked at 49.8% in April, Delhi at 42.3% in May and Maharashtra at 20.9% in April. Delhi stayed above 12% until September, while Maharashtra and Tamil Nadu recovered faster.
- **The North and East had the highest average unemployment, and the West the lowest.**
- **The three indicators are only weakly correlated** (between -0.25 and -0.05), so the heatmap alone does not show strong links.

## How to Run
1. Clone this repository or download the folder.
2. Install the libraries:
   ```
   pip install pandas numpy matplotlib seaborn jupyter
   ```
3. Keep `Unemployment_Rate_upto_11_2020.csv` in the same folder as the notebook. In the loading cell, use `pd.read_csv('Unemployment_Rate_upto_11_2020.csv')` (the notebook may use a Google Colab path starting with `/content/`).
4. Open `DataScience-Task2-UnemploymentAnalysis.ipynb` in Jupyter Notebook or Google Colab and run all cells from top to bottom.

## Project Structure
```
DataScience-Task2-UnemploymentAnalysis/
├── DataScience-Task2-UnemploymentAnalysis.ipynb   # Full analysis
├── Unemployment_Rate_upto_11_2020.csv             # Dataset
└── README.md                                      # Project description
```

## Limitations
- The data covers only ten months of 2020, and the pre-COVID period is just two months.
- Averages are simple averages across states and are not weighted by population, so they are not the official national unemployment rate.
- Three months have 26 states instead of 27.
- The analysis shows patterns, not proof of what caused them.

## Possible Next Steps
- Compare with 2019 data to separate seasonal patterns from the COVID effect.
- Weight state averages by labour force size.
- Compare rural and urban unemployment using the larger version of the dataset.

## Tech Stack
Python, pandas, matplotlib, seaborn, Jupyter Notebook

## Author
**Hanifah Morayo Abdulazeez**
LinkedIn: www.linkedin.com/in/hanifahmorayoabdulazeez

Completed as part of the Oasis Infobyte Data Science Internship (#oasisinfobyte).
