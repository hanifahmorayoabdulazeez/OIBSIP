# Iris Flower Classification

A machine learning project that identifies the species of an iris flower (Setosa, Versicolor or Virginica) from its physical measurements. Built as Task 1 of the Oasis Infobyte Data Science internship (OIBSIP).

## Objective
Train and compare classification models that predict an iris flower's species from its sepal and petal measurements, and check that the results are reliable using cross-validation.

## Dataset
The Iris dataset, which is built into scikit-learn (no download needed).

| Detail | Value |
|---|---|
| Flowers | 150 (50 per species) |
| Features | Sepal length, sepal width, petal length, petal width (all in cm) |
| Target | Species: Setosa, Versicolor, Virginica |
| Missing values | None |
| Duplicate rows | 1 (kept, because it is a real measurement) |

## Approach
1. **Load and prepare the data:** loaded the dataset, replaced the species numbers with names, and renamed the columns.
2. **Data check:** checked the shape, data types, missing values, duplicates and class balance.
3. **Visualisation:** a pairplot and box plots to see how the species differ on each measurement.
4. **Train/test split:** 80% training (120 flowers) and 20% testing (30 flowers), stratified so each species is equally represented.
5. **Modelling:** trained Logistic Regression and K-Nearest Neighbours (k = 5).
6. **Evaluation:** accuracy, confusion matrix, precision, recall and F1-score on the test set.
7. **Cross-validation:** 5-fold stratified cross-validation to check that the results were not due to a lucky split.
8. **Prediction:** used the final model on a new flower that is not in the dataset.

## Results

**On the test set (30 flowers)**

| Model | Accuracy | Mistakes |
|---|---|---|
| Logistic Regression | 96.67% | 1 out of 30 |
| K-Nearest Neighbours | 100% | 0 out of 30 |

**5-fold cross-validation (all 150 flowers)**

| Model | Mean accuracy |
|---|---|
| Logistic Regression | 96.67% (±2.98%) |
| K-Nearest Neighbours | 96.67% (±2.98%) |

## Key Findings
- **Setosa is easy to identify.** It forms its own group and was classified perfectly by both models.
- **Versicolor and Virginica overlap slightly.** They are the only species the models confuse (Logistic Regression's single mistake was one Versicolor predicted as Virginica).
- **Petal measurements separate the species best.** Petal length and petal width are more useful than sepal measurements.
- **KNN's 100% was a lucky split.** In cross-validation both models score the same (96.67%), so there is no meaningful difference between them.
- **Recommended model: Logistic Regression.** It performs just as well as KNN, is simpler, trains faster, and is easier to explain.

## Example Prediction
For a new flower with sepal length 6.0 cm, sepal width 2.9 cm, petal length 4.5 cm and petal width 1.5 cm, the model predicts **Versicolor** with about 79% confidence (and about 20% for Virginica), reflecting the overlap between these two species.

## How to Run
1. Clone this repository or download the folder.
2. Install the libraries:
   ```
   pip install pandas matplotlib seaborn scikit-learn jupyter
   ```
3. Open `DataScience-Task1-IrisClassification.ipynb` in Jupyter Notebook or Google Colab and run all cells from top to bottom.

## Project Structure
```
DataScience-Task1-IrisClassification/
├── Iris_Classification.ipynb   # Full analysis and models
└── README.md                   # Project description
```

## Limitations
- The Iris dataset is small and its classes are well separated, so real-world data would likely give lower scores and need more tuning and validation.
- Only two models were compared, with default settings and no hyperparameter tuning.

## Tech Stack
Python, pandas, scikit-learn, matplotlib, seaborn, Jupyter Notebook

## Author
**Hanifah Morayo Abdulazeez**
LinkedIn: www.linkedin.com/in/hanifahmorayoabdulazeez

Completed as part of the Oasis Infobyte Data Science Internship (#oasisinfobyte).
