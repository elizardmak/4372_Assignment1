# CS 4372 - Assignment 1

Elizaveta Makhonina: NetID - dal445515
Avizeh Walji: NetID - anw230000

Overview:
This project builds & compares two regularized linear regression approaches on the Facebook Comment Volume Dataset from the UCI Machine Learning Repository (Dataset ID 363, 1st Variant).

The project implements:
1. SGDRegressor from scikit-learn, with hyperparameter tuning across penalty type, alpha, L1 ratio, learning rate, maximum iterations, and loss function.

2. OLS and Regularized OLS using Statsmodels. OLS is first fitted using .fit() to obtain full regression diagnostics, followed by regularized OLS using .fit_regularized() with different values of alpha and L1 weight.

The task is a regression problem: predicting the number of comments a Facebook post will receive over the next H hours using predictor variables describing the page, post, and comment activity available at the observation time.

Files within the submission:
assignment1.ipynb: complete Python/Jupyter Notebook containing data loading, preprocessing, feature selection, both regression approaches, hyperparameter experiments, evaluation, and plots.
4372_Assignment1_Report.pdf:	written report containing the tables, plots, results, and interpretation.
README.md:	project description, requirements, assumptions, and instructions for running the notebook.

Requirements:
Python 3.9+ with: NumPy, Pandas, Matplotlib, Seaborn, SciPy, Scikit-learn, Statsmodels, ucimlrepo

Running the assignment:
The notebook loads the dataset from a public GitHub raw CSV URL
1. open assignment1.ipynb in Jupyter Notebook / Google Colab.
2. run the notebook cells from top to bottom.
3. the code performs preprocessing, feature selection, model training, hyperparameter tuning, evaluation, and visualization.

Method summary:
- Missing/inconsistent data and duplicate records are checked during preprocessing.
- Categorical page_category values are grouped and one-hot encoded.
- The data is split into 80% training / 20% testing with random_state=42.
- Top 10 numerical predictors are selected using absolute correlation with the target, computed from the training split only.
- Numerical features are standardized using StandardScaler, fit on the training data only and then applied to the test data.
- SGDRegressor hyperparameters include penalty, alpha, L1 ratio, learning rate, iterations, and loss.
- OLS is evaluated with full statistical diagnostics.
- Regularized OLS is tuned over alpha and L1_wt.
  
Reproducibility:
RANDOM_STATE = 42
TEST_SIZE = 0.20
TOP_N_CATEGORIES = 15
N_FEATURES = 10
The scaler is fitted only on the training data and then applied to the test data. 

Assumptions:
Dataset: The UCI Facebook Comment Volume Dataset (ID 363, Variant 1) was used, with 8 duplicate rows removed during preprocessing.
Categorical variables: page_category is treated as a categorical feature. The 15 most frequently occurring categories are retained individually, while all remaining categories are combined into an "other" group.
Feature selection: The top 10 features based on their absolute correlation with the target are identified using only the training data. This prevents the test set from influencing predictor selection.
Normalization: Standardization using StandardScaler is used as the normalization method for this assignment. No separate Min-Max scaling is performed.
Derived features: derived_agg_1 through derived_agg_25 retain their original UCI dataset names because the available documentation does not indicate which specific statistics they represent.
