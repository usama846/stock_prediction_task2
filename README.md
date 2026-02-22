# Task 2: Predict Future Stock Prices (Short-Term)

## Task Objective
Build a machine learning model to predict the next day's stock closing price using historical OHLCV (Open, High, Low, Close, Volume) data from Yahoo Finance.

## Dataset Used
- **Source**: Yahoo Finance (via `yfinance` library)
- **Stock**: Tesla Inc. (TSLA)
- **Period**: 2020-01-01 to Present
- **Features**: Open, High, Low, Volume
- **Target**: Next day's Closing Price

## Project Workflow and Screenshots

### 1. Data Loading and Inspection
**Screenshot**: Head

Displays the first few rows of the raw TSLA dataset showing Open, High, Low, Close, and Volume columns before preprocessing.

### 2. Data Cleaning and Preprocessing
**Screenshot**: Data_Cleaning

Shows the data cleaning process including:
- Flattening multi-level column names (removing 'TSLA' suffix)
- Handling missing values
- Creating the target variable `Next_Close`
- Dataset shape after preprocessing

---

### 3. Data Visualization and Exploration

#### 3.1 TSLA Stock Price History
**Screenshot: `Data_Visualization01`**

Line plot showing TSLA's historical closing price from 2020 to present, illustrating:
- Overall upward trend
- Periods of high volatility
- Significant price movements and corrections

#### 3.2 Feature Correlation Matrix
**Screenshot: `Data_Visualization02`**

Heatmap displaying correlation between all features (Open, High, Low, Close, Volume, Next_Close):
- Strong positive correlations between OHLC features
- Volume shows weaker correlation with price
- Close and Next_Close show high correlation (expected)

#### 3.3 Actual vs Predicted Prices
**Screenshot: `Data_Visualization03`**

Comparison plot showing:
- Actual TSLA closing prices (black line)
- Linear Regression predictions (dashed line)
- Random Forest predictions (dotted line)
- Visual assessment of model fit

#### 3.4 Residual Analysis
**Screenshot: `Data_Visualization04`**

Residual plots for both models:
- Linear Regression residuals distribution
- Random Forest residuals distribution
- Helps identify patterns in prediction errors

---

### 4. Feature Statistics
**Screenshot: `Feature_Statistics`**

Statistical summary table showing:
- Count, mean, standard deviation for each feature
- Minimum and maximum values
- 25th, 50th (median), and 75th percentiles
- Helps understand data distribution and scale

---

### 5. Model Training and Evaluation

#### 5.1 Linear Regression Results
**Screenshot: `Linear_Regression`**

Output showing Linear Regression model performance:
- Model coefficients for each feature
- R² Score: 0.961 (96.1% accuracy)
- RMSE: $13.57
- MAE: $10.70
- Feature importance (coefficients)

#### 5.2 Random Forest Results
**Screenshot: `Random_Forest`**

Output showing Random Forest model performance:
- Feature importance rankings
- R² Score: 0.810 (81.0% accuracy)
- RMSE: $29.93
- MAE: $22.56
- Number of estimators and parameters used

---

### 6. Model Comparison and Analysis

#### 6.1 TSLA Stock Price Prediction Summary
**Screenshot: `TSLA_Stockprice_Prediction`**

Overall summary visualization combining:
- Historical price context
- Prediction overlay
- Model performance highlights
- Key statistics

#### 6.2 Detailed Model Comparison
**Screenshot: `Detailed_Comparison`**

Side-by-side comparison showing:
- Prediction curves for both models
- Error distributions
- Performance metrics visualization
- Strengths and weaknesses of each approach

#### 6.3 Final Model Comparison Table
**Screenshot: `Model_Comparison`**

Quantitative comparison table:

| Metric | Linear Regression | Random Forest |
|--------|-------------------|---------------|
| **RMSE** | $13.57 | $29.93 |
| **MAE** | $10.70 | $22.56 |
| **R² Score** | 0.961 | 0.810 |

---

## Key Results and Findings

### Best Performing Model: Linear Regression
- **Accuracy**: 96.1% (R² = 0.961)
- **Average Error**: $10.70 (MAE)
- **Why it works**: TSLA exhibits strong linear trends in price movement; today's OHLC values are highly predictive of tomorrow's close

### Random Forest Performance
- **Accuracy**: 81.0% (R² = 0.810)
- **Average Error**: $22.56 (MAE)
- **Limitation**: Overfits to noise in TSLA's volatile price movements

### Key Insights
1. Linear models excel at capturing TSLA's trend-following behavior
2. OHLC features contain sufficient information for next-day prediction
3. Volume has lower predictive power compared to price-based features
4. Model error of ~$10-14 represents 3-5% of typical TSLA price range

---

## Limitations

- **Short-term only**: Predicts 1 day ahead; accuracy degrades for longer horizons
- **No external factors**: Market news, earnings reports, social media sentiment not included
- **Historical bias**: Model trained on past data may not predict future market regime changes

- **Volatility periods**: Extreme price swings may temporarily reduce prediction accuracy

