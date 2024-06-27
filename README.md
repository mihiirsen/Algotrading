# Trading Model Documentation

## Overview:
We developed a predictive trading model as part of the KGP Data Science Hackathon. The goal was to create a system that predicts whether the closing parameter of a stock will increase or decrease, utilizing various indicators and machine learning techniques.

## Methodology:
### Problem Statement:
The hackathon problem statement revolved around real-time trading strategies.

### Model Development:
- **Prediction Model:** We developed a model that predicts the direction of the Close parameter (increase or decrease) based on the current day's data. The model employs a binary classification approach.
- **Indicators Used:**
  1. **RSI (Relative Strength Index):** Identifies overbought or oversold conditions.
  2. **MACD (Moving Average Convergence Divergence):** Shows the relationship between two moving averages.
  3. **Stochastic Oscillator:** Measures overbought or oversold conditions.
  4. **Momentum:** Indicates the rate of change of closing price.
  5. **Moving Average (MA):** Smoothes out fluctuations to identify trends.
  6. **ATR (Average True Range):** Measures market volatility.
  7. **Lagged ATR:** Previous day's ATR values.

### Model Training:
- We used an XGBoost Classifier for training, excluding provided features like open, close, high, low, and volume.
- Achieved an approximate accuracy of 83%.

### Backtesting Results:
- Evaluated model performance through various metrics.
- Manual calculation of metrics such as largest losing trade, gross profit, net profit, etc.
- Backtesting to assess the model's performance in a simulated trading environment.

### Trading Strategy:
- Implemented a binary classification model predicting stock price movement.
- Entered trades based on model predictions with specific risk management rules.
- Caution and ongoing monitoring advised due to the complexity of stock price prediction.

### Visualization:
- Used lime plots for local interpretable model-agnostic explanations.
- Utilized SHAP (SHapley Additive exPlanations) values for feature importance.

## Metrics and Results:
- Documented various metrics, including largest losing trade, gross profit, net profit, close trades, open trades, max drawdown, etc.
- Highlighted key ratios such as Sharpe Ratio and Sortino Ratio for risk-adjusted returns.

## Trading Scenarios:
- Outlined different trading scenarios based on model predictions.
- Described approaches for managing ongoing trades during changing market conditions.

## Conclusion:
- The developed model showcased promising results in backtesting.
- Emphasized the complexity of stock price prediction and the need for caution in real-world financial applications.

# Additional Trading Scenarios
In addition to our primary trading strategy, we have developed alternative scenarios to adapt to changing market conditions.

## Scenario 1: Reinforcing an Uptrend
- **Condition:** Before closing an ongoing increasing trade, if the model predicts a price increase in the next hour.
- **Action:**
  - Retain a portion of holdings to continue in the market.
  - Add more funds to reinforce the position for the anticipated uptrend.
  - Sell another portion of holdings to secure profits.

## Scenario 2: Switching Positions during an Uptrend to Downtrend
- **Condition:** Holding two shares during an uptrend, and the model signals a downtrend.
- **Action:**
  - Close the entire long position.
  - Enter a short position by purchasing some shares at a rate of 0.05%.

## Scenario 3: Adjusting Short Position during a Downtrend
- **Condition:** During a downtrend, if the model forecasts a continued downtrend.
- **Action:**
  - Close a portion of the short position to capture profits.
  - Retain the remaining shares in the short position.
  - Strengthen the short position by selling additional shares.

## Scenario 4: Transitioning from Downtrend to Uptrend
- **Condition:** In a downtrend where the model predicts an uptrend in the next hour.
- **Action:**
  - Fully close the short position.
  - Enter a long position using a portion of our capital, aligning with the model's forecast of an upcoming uptrend.

# Backtesting Results and Required Metrics
## Backtesting Results:
We manually calculated various metrics to evaluate the performance of our trading model during the backtesting period.

1. **Largest Losing Trade (loss_mag_max):**
   - The maximum magnitude of a losing trade during the backtesting period.

2. **Gross Profit:**
   - Cumulative profit before deducting transaction costs.

3. **Net Profit:**
   - Cumulative profit after deducting transaction costs.

4. **Close Trades (trades):**
   - The total number of trades executed (both profitable and losing).

5. **Open Trades:**
   - The number of currently open trades at the end of the backtesting period.

6. **Max Drawdown:**
   - The maximum percentage loss from a peak to a trough in the equity curve.

7. **Maximum Loss:**
   - The largest loss in percentage terms from all the losing trades.

8. **Average Losing Trade:**
   - The average percentage loss per losing trade.

9. **Average Winning Trade:**
   - The average percentage profit per winning trade.

10. **Buy and Hold Return:**
    - The percentage return if one bought and held the asset throughout the entire period.

11. **Largest Winning Trade:**
    - The largest profit in percentage terms from all the winning trades.

12. **Average Holding Duration per Trade:**
    - The average duration a trade is held.

13. **Sharpe Ratio:**
    - A measure of risk-adjusted return, indicating the excess return per unit of risk.

14. **Sortino Ratio:**
    - Similar to Sharpe Ratio, but it only considers downside risk.

15. **Max Dip:**
    - The maximum percentage decline in the price-earnings ratio.

16. **Average Dip:**
    - The average percentage decline in the price-earnings ratio.

## Required Metrics:
Here are the specific metrics and results obtained from our backtesting:

- **Largest Losing Trade:** 88.64483584068014
- **Gross Profit:** 50380.069525745006
- **Net Profit:** 50304.49942145645
- **Close Trades:** 8897
- **Open Trades:** 0
- **Max Drawdown:** -6.444691630072064
- **Maximum Loss:** 88.64483584068014
- **Average Losing Trade:** 3.3456664361396777
- **Average Winning Trade:** 7.380354962068141
- **Buy and Hold Return:** 102.85230883821612
- **Largest Winning Trade:** 89.13005507608007
- **Average Holding Duration per Trade:** 1
- **Sharpe Ratio:** 0.5972699637914145
- **Sortino Ratio:** 2.1006085691715244
- **Max Dip:** 99.9487972778143
- **Average Dip:** -3.94007930686994

These metrics provide insights into the performance, risk, and profitability of our trading model during the
