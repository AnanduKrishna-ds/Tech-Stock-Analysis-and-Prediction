Tech Stock Analysis and Prediction
A data science project analyzing NVDA stock returns across both regression and classification frameworks, comparing machine learning approaches and evaluating their limits in the context of financial market efficiency.

Project Overview
This project approaches stock prediction from two angles — predicting return magnitude (regression) and predicting price direction (classification) — across 1,984 NVDA trading days from 2018 to 2025. The analysis includes:

Exploratory Data Analysis of 5 major tech stocks
Feature engineering with lag features and rolling volatility measures
Systematic benchmarking of Naive Baseline, Linear Regression, Random Forest, and XGBoost models
Binary direction classification (Up/Down) with ROC curve and confusion matrix evaluation
Honest interpretation of results through the lens of the Efficient Market Hypothesis


Project Structure
Tech-Stock-Analysis-and-Prediction/
│
├── data/
│   ├── raw_data.csv              # Original stock data
│   ├── cleaned_data.csv          # Preprocessed data
│   └── nvda_cleaned.csv          # NVDA-specific cleaned data
│
└── Notebooks/
    ├── 01_eda.ipynb              # Exploratory Data Analysis
    ├── 02_preprocessing.ipynb    # Data validation and cleaning
    ├── 03_naive_baseline.ipynb   # Naive persistence model
    ├── 04_linear_regression.ipynb# Linear regression model
    ├── 05_random_forest.ipynb    # Random Forest ensemble
    ├── 06_xgboost.ipynb          # XGBoost gradient boosting
    └── 07_classification.ipynb   # Direction classification with ROC & confusion matrix

Regression Results — Return Magnitude Prediction
ModelMSERMSEMAER² ScoreNaive Baseline0.0023040.0479960.034369-1.2744Linear Regression0.0009980.0315870.0227940.0149Random Forest0.0004570.0213870.017306-0.0511XGBoost0.0010410.0322580.023208-0.0274
Key Findings

Random Forest achieved the lowest error metrics (MSE: 0.000457, MAE: 0.017306) making it the best regression performer despite a negative R²
Linear Regression was the only model with a positive R² (0.0149) — the only model to outperform the mean baseline
XGBoost performed worse than Random Forest, demonstrating that model complexity does not guarantee better performance on noisy financial data
All ML models outperformed the naive baseline, validating the value of machine learning even on difficult prediction problems
Feature importance analysis revealed lag4 (4-day prior return) as the strongest predictor, though importance was distributed fairly evenly across all features


Classification Results — Direction Prediction (Up/Down)
Binary classification extension predicting whether NVDA will move Up or Down the next trading day.
ModelAUCAccuracyF1 ScoreLogistic Regression0.59158%0.58Random Forest0.49450%0.49
Key Findings

Logistic Regression outperformed Random Forest in both AUC and accuracy — consistent with regression findings where simpler models handled financial noise better
Random Forest AUC of 0.494 is essentially random, confirming it captures no meaningful directional signal
58% accuracy for Logistic Regression represents a modest but genuine signal above the 50% random baseline
Results across both regression and classification consistently support the Efficient Market Hypothesis — daily stock movements are largely unpredictable from historical returns alone


Why Negative R² and Near-Random Classification Are Expected
The Efficient Market Hypothesis (EMH) suggests that stock prices already reflect all available information, making future price movements largely unpredictable from historical data alone. Our results across both regression and classification consistently support this:

Daily returns exhibit high noise and weak autocorrelation
Past returns have minimal predictive power for future returns
Even sophisticated models like XGBoost and Random Forest cannot overcome fundamental market randomness

The near-random results are not a failure — they are an honest finding aligned with decades of financial research. Knowing when a problem is inherently difficult is as valuable as finding the best model.

Methodology
Data: NVDA stock, February 2018 – December 2025, 1,984 trading days
Features: 5 lag features (lag1–lag5) + Rolling Standard Deviation (volatility)
Train/Test Split: Chronological 80/20 split with no shuffle to prevent data leakage
Regression Metrics: MSE, RMSE, MAE, R², residual analysis, feature importance, actual vs predicted plots
Classification Metrics: ROC curves, AUC, confusion matrix, precision, recall, F1 score, class imbalance handling via class_weight='balanced'

Technologies Used

Language: Python 3.10
Data Analysis: Pandas, NumPy
Visualization: Matplotlib, Seaborn
Machine Learning: Scikit-learn, XGBoost
Data Source: yfinance


How to Run
Clone the repository:
bashgit clone https://github.com/AnanduKrishna-ds/Tech-Stock-Analysis-and-Prediction.git
cd Tech-Stock-Analysis-and-Prediction
Install dependencies:
bashpip install pandas numpy matplotlib seaborn scikit-learn xgboost yfinance
Run notebooks in order from 01 through 07.

Lessons Learned

Domain knowledge matters — understanding EMH and random walk theory is essential to interpret financial ML results correctly
Simpler models can win — Logistic Regression outperformed Random Forest in classification just as Linear Regression held its own in regression
Proper evaluation is critical — time series data requires chronological splits to avoid data leakage
Honest reporting — negative and near-random results are findings, not failures
Consistency across frameworks — regression and classification findings told the same story, strengthening the overall conclusion


Author
Anandu Krishna
GitHub: AnanduKrishna-ds

License
This project is open source and available under the MIT License.
