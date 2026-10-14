# Value and Wage Prediction: Football Players

A Machine Learning project focused on predicting football players' market value and wages using regression algorithms.

**Academic Year:** 2024/2025  
**Course:** Machine Learning Project  

## Authors

- Matteo Hu — 23094
- Laraib Ahmed — 22509
- Stefano Pugnani — 22582

## Project Overview

The goal of this project is to develop and compare machine learning models capable of predicting two important economic indicators for football players:

- **Market Value:** the estimated transfer market value of a player.
- **Wage:** the player's salary.

The project explores different regression approaches to understand how players' physical attributes, technical skills, performance statistics, and other characteristics relate to their market value and wages.
## Project Report

The complete project report is available in PDF format and provides a detailed description of the methodology, implementation, experiments, and results.

📄 **[Read the Full Project Report (PDF)](./nome_file.pdf)**

The report covers:

- Dataset description and feature selection
- Data preprocessing and encoding techniques
- Exploratory Data Analysis (EDA)
- Multi-output and multi-task regression algorithms
- Hyperparameter optimization using GridSearchCV
- Model evaluation and R² score comparison
- Final considerations and conclusions
  
## Dataset

The project uses the *Football Player's Market Value* dataset, available on GitHub:

[Football Player's Market Value Dataset](https://github.com/Bouaskaoun/Football-Player-s-Market-Value/blob/main/player_list.csv)

Dataset characteristics:

- **Number of samples:** 17,780
- **Number of features:** 64
- **Target variables:** Value and Wage

The dataset includes several categories of information:

- **Personal attributes:** age, height, weight, and preferred foot.
- **Performance indicators:** overall rating, potential, and technical skills.
- **Player statistics:** attacking, defending, movement, power, mentality, and goalkeeping attributes.
- **Club information:** team and release clause.
- **Aggregated statistics:** total stats, base stats, and FIFA attributes such as PAC, SHO, PAS, DRI, DEF, and PHY.

## Data Preprocessing

Several preprocessing techniques were applied to prepare the dataset for model training.

### Feature Selection

Relevant numerical and categorical features were selected based on their potential relationship with market value and wages.

### Encoding

- **One-Hot Encoding:** applied to categorical features such as foot and position, avoiding the introduction of artificial ordinal relationships.
- **Frequency Encoding:** applied to the team feature to represent clubs according to their frequency in the dataset, avoiding the large number of features that One-Hot Encoding would produce.

### Standardization

Standardization was used to make numerical features comparable in scale and prevent variables with larger numerical ranges from dominating the learning process.

### Exploratory Data Analysis

Exploratory Data Analysis (EDA) was performed using:

- Histograms to examine the distributions of market value and wages.
- Box plots to compare player values and wages across positions.
- Correlation heatmaps to investigate relationships between numerical attributes.

The analysis highlighted strong correlations between market value, wages, and release clauses. Overall rating and potential also showed relevant relationships with these economic indicators.

## Machine Learning Models

Six regression approaches were implemented and compared.

### Multi-Output Regression

The `MultiOutputRegressor` wrapper was used to adapt standard regression algorithms to predict both target variables.

| Model | Description |
|---|---|
| Linear Regression | Linear baseline model |
| Ridge Regression | Linear regression with L2 regularization |
| Decision Tree Regressor | Non-linear model based on decision rules |
| Support Vector Regressor (RBF) | Non-linear regression using an RBF kernel |

### Multi-Task Regression

Multi-task models learn to predict multiple target variables jointly.

| Model | Description |
|---|---|
| MultiTaskLasso | L1 regularization for feature selection and sparsity |
| MultiTaskElasticNet | Combination of L1 and L2 regularization |

## Hyperparameter Optimization

Hyperparameter tuning was performed using `GridSearchCV` with 3-fold cross-validation.

The dataset was split into training and test sets using an **80/20 split**.

The following hyperparameters were optimized:

| Model | Hyperparameters |
|---|---|
| Decision Tree Regressor | `max_depth`, `min_samples_split` |
| Ridge Regression | `alpha` |
| SVR (RBF) | `C`, `epsilon` |
| MultiTaskLasso | `alpha` |
| MultiTaskElasticNet | `alpha`, `l1_ratio` |
| Linear Regression | No hyperparameters tuned |

The best configurations reported in the project included:

- **Decision Tree:** `max_depth = 5`, `min_samples_split = 4`
- **Ridge Regression:** `alpha = 5.0`
- **SVR:** `C = 100`, `epsilon = 0.1`
- **MultiTaskLasso:** `alpha = 0.01`
- **MultiTaskElasticNet:** `alpha = 0.01`, `l1_ratio = 0.1`

## Evaluation Metric

Model performance was evaluated using the **coefficient of determination (R²)**.

R² measures how well a regression model explains the variance of the target variables.

- **R² = 1:** perfect predictions.
- **R² = 0:** performance equivalent to predicting the target mean, under the standard definition.
- **R² < 0:** performance worse than the mean-prediction baseline.

Higher R² scores indicate better predictive performance.

## Results

The following table reports the R² scores obtained on the test set.

| Rank | Model | R² Score |
|---:|---|---:|
| 1 | Decision Tree Regressor | 0.9139 |
| 2 | SVR (RBF Kernel) | 0.8967 |
| 3 | Linear Regression | 0.8524 |
| 4 | Ridge Regression | 0.8519 |
| 5 | MultiTaskElasticNet | 0.8510 |
| 6 | MultiTaskLasso | 0.8503 |

### Main Findings

- The **Decision Tree Regressor** achieved the highest reported R² score of **0.9139**.
- The **SVR with an RBF kernel** achieved the second-best result, with an R² score of **0.8967**.
- Both non-linear models outperformed the linear and multi-task regression approaches in the reported experiments.
- The multi-output approaches performed better than the multi-task models on this dataset.
- Hyperparameter optimization was particularly useful for improving the performance of selected models, especially SVR.

These results suggest that non-linear relationships between player attributes and economic indicators play an important role in predicting market value and wages.

## Technologies

The project uses Python-based machine learning techniques and the following tools and libraries:

- Python
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- Seaborn

## Repository Contents

The repository contains the project implementation and its documentation, including the report describing the dataset, preprocessing pipeline, regression models, hyperparameter optimization, evaluation results, and final comparison.


**Machine Learning Project — Academic Year 2024/2025**  
