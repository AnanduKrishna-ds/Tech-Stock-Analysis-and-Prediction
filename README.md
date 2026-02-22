# 📊 Tech Stock Analysis and Prediction

A comprehensive data science project analyzing NVDA stock returns and comparing machine learning approaches for price prediction.

---

## 🎯 Project Overview

This project explores the predictive power of different machine learning models on NVDA (NVIDIA) stock returns from 2018-2025. The analysis includes:

* Exploratory Data Analysis of 5 major tech stocks
* Feature engineering with lag features and volatility measures
* Systematic comparison of Naive Baseline, Linear Regression, Random Forest, and XGBoost models
* Honest evaluation of model performance in the context of financial market efficiency

---

## 📁 Project Structure

```
Tech-Stock-Analysis-and-Prediction/
│
├── data/                          # All datasets
│   ├── raw_data.csv              # Original stock data
│   ├── cleaned_data.csv          # Preprocessed data
│   └── nvda_cleaned.csv          # NVDA-specific cleaned data
│
└── Notebooks/
    ├── 01_eda.ipynb              # Exploratory Data Analysis
    ├── 02_preprocessing.ipynb     # Data validation and cleaning
    ├── 03_naive_baseline.ipynb    # Naive persistence model
    ├── 04_linear_regression.ipynb # Linear regression model
    ├── 05_random_forest.ipynb     # Random Forest ensemble
    └── 06_xgboost.ipynb           # XGBoost gradient boosting
```

---

## 🔍 Key Findings

### Model Performance Comparison

| Model | MSE | RMSE | MAE | R² Score |
|-------|-----|------|-----|----------|
| Naive Baseline | 0.002304 | 0.047996 | 0.034369 | -1.2744 |
| Linear Regression | 0.000998 | 0.031587 | 0.022794 | **0.0149** |
| Random Forest | **0.000457** | 0.021387 | **0.017306** | -0.0511 |
| XGBoost | 0.001041 | 0.032258 | 0.023208 | -0.0274 |

### Insights

1. **All models struggled with daily return prediction** (negative or near-zero R² scores), which aligns with the Efficient Market Hypothesis—daily stock returns are largely unpredictable

2. **Random Forest achieved the lowest error metrics** (MSE: 0.000457, MAE: 0.017306), making it the best performer despite a negative R²

3. **Linear Regression had the only positive R²** (0.0149), indicating it was the only model to outperform the mean baseline, though it explains less than 2% of variance

4. **Model complexity ≠ better performance**: XGBoost (gradient boosting) performed worse than Random Forest (bagging), demonstrating that more sophisticated algorithms cannot overcome fundamental market randomness

5. **Feature importance revealed weak patterns**: lag4 (4-day prior return) was most important for tree-based models, but overall feature importance was distributed fairly evenly, indicating no single strong predictor

6. **All ML models beat naive baseline**: Even the weakest ML approach significantly outperformed the "repeat yesterday" strategy, validating the value of machine learning techniques

---

## 🛠️ Technologies Used

* **Python 3.10**
* **Data Analysis**: Pandas, NumPy
* **Visualization**: Matplotlib, Seaborn
* **Machine Learning**: Scikit-learn, XGBoost
* **Data Source**: yfinance

---

## 🚀 How to Run

1. **Clone the repository:**
```bash
git clone https://github.com/AnanduKrishna-ds/Tech-Stock-Analysis-and-Prediction.git
cd Tech-Stock-Analysis-and-Prediction
```

2. **Install dependencies:**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost yfinance
```

3. **Run notebooks in order:**
   * Start with `01_eda.ipynb` for data exploration
   * `02_preprocessing.ipynb` for data validation and cleaning
   * Then run model notebooks: `03_naive_baseline.ipynb` → `04_linear_regression.ipynb` → `05_random_forest.ipynb` → `06_xgboost.ipynb`

---

## 📈 Methodology

### Data
* **Stock**: NVDA (NVIDIA)
* **Period**: February 2018 - December 2025 (1,984 trading days)
* **Features**: 5 lag features (past returns) + Rolling Std (volatility)
* **Target**: Daily returns

### Model Progression
1. **Naive Baseline**: Persistence model (tomorrow = today)
2. **Linear Regression**: Simple linear relationships
3. **Random Forest**: Ensemble bagging approach
4. **XGBoost**: Gradient boosting with hyperparameter tuning

### Evaluation
* **Train/Test Split**: 80/20 chronological split (no shuffle to prevent data leakage)
* **Metrics**: MSE, RMSE, MAE, R²
* **Validation**: Residual analysis, feature importance, actual vs predicted plots

---

## 💡 Why Negative R² Scores Are Expected

This project demonstrates an important reality of financial prediction:

**The Efficient Market Hypothesis (EMH)** suggests that stock prices already reflect all available information, making future price movements largely unpredictable from historical data alone. Our results support this theory:

* Daily returns exhibit **high noise** and **weak autocorrelation**
* Past returns have **minimal predictive power** for future returns
* Even sophisticated models like XGBoost cannot overcome this fundamental randomness

**The negative R² scores are not a failure**—they are an honest finding that aligns with decades of financial research. This project shows that knowing when a problem is inherently difficult is as valuable as finding the best solution.

---

## 🎓 Lessons Learned

1. **Domain knowledge matters**: Understanding financial markets (EMH, random walk theory) helps interpret results correctly
2. **Simpler models can win**: Random Forest outperformed XGBoost; complexity doesn't guarantee better performance
3. **Proper evaluation is critical**: Time series require chronological splits to avoid data leakage
4. **Honesty in reporting**: Negative results teach us about problem difficulty, not model failure
5. **Feature engineering limitations**: Even well-designed features (lags, volatility) provide minimal signal in noisy financial data

---

## 📊 Future Work

* Expand dataset to 10+ years for better generalization
* Explore direction prediction (classification: Up/Down) instead of magnitude
* Incorporate additional features:
  * Trading volume
  * Market sentiment (news, social media)
  * Macroeconomic indicators (interest rates, GDP)
* Test longer prediction horizons (weekly/monthly returns)
* Implement ensemble stacking methods

---

## 👤 Author

**Anandu Krishna**
* GitHub: [AnanduKrishna-ds](https://github.com/AnanduKrishna-ds)

---

## 📝 License

This project is open source and available under the MIT License.

---

## 🙏 Acknowledgments

* Data provided by Yahoo Finance via yfinance
* Inspired by research on the Efficient Market Hypothesis (Eugene Fama)
* Special thanks to the open-source community for the incredible tools that made this analysis possible

---

**⭐ If you found this project interesting or learned something from it, please consider giving it a star!**
