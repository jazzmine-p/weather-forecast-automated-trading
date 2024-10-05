# Weather Forecasting and Automated Trading System

## Overview
This project integrates deep learning weather forecasting with an automated trading system using Kalshi’s API. The goal was to predict daily weather conditions and use those predictions to automate trades on Kalshi's prediction markets. By employing a Long Short-Term Memory (LSTM) model to forecast weather and using a strategic trading approach, the system achieved a **20% profit in one week**.

### Key Features:
- **Deep Learning Weather Forecasting**: Built and trained LSTM models to predict daily weather conditions, accounting for seasonality and temporal dependencies.
- **Automated Trading via Kalshi API**: Implemented a system that automates trades based on daily weather forecasts.
- **Strategic Trading Logic**: Developed a trading strategy to optimize risk based on forecasted temperature ranges.
- **Data Pipeline**: Collected and processed data from multiple sources to ensure accurate predictions and trading actions.

---

## Project Components

### 1. Data Collection
The project pulled and evaluated weather data from five different sources, including:
- National Centers for Environmental Information (NCEI)
- National Oceanic and Atmospheric Administration (NOAA)

### 2. Long Short-Term Memory
An LSTM model was used to predict daily weather conditions due to its ability to handle sequential data and long-range dependencies.

- **Model Choice Rationale**
  1. **Sequential Nature**: Weather data is inherently sequential, with past conditions affecting future ones. LSTM is well-suited to handle time-series data and capture these dependencies.
  2. **Multivariate Input**: LSTM can handle multiple variables such as temperature, precipitation, and wind speed, allowing the model to capture complex relationships.
  3. **Seasonality**: LSTM is effective at recognizing seasonal trends and temporal patterns in weather data.

- **Model Training & Evaluation**: 
  - The LSTM model was trained on historical weather data, and early stopping was implemented to prevent overfitting and save computational resources. Training was halted when validation loss began to degrade, ensuring optimal model performance.

### 3. Automated Trading System
The automated trading system places bets on Kalshi’s prediction markets based on the LSTM model's forecasts.

Kalshi is a regulated prediction market platform that allows users to trade on the outcome of real-world events. It operates similarly to a stock exchange, but instead of trading shares, users buy and sell positions on the likelihood of specific events occurring. As a Commodity Futures Trading Commission (CFTC) regulated platform, Kalshi provides a legal and secure environment for users to speculate on events by placing "yes" or "no" bets, with payouts determined by the eventual outcome.

- **Kalshi API Integration**:
  - The system connects to Kalshi’s API to automate daily trading decisions.
  - Trades are placed on specific weather-related events, such as temperature ranges.

- **Trading Strategy**:
  - Given the one-degree Fahrenheit specificity required by Kalshi’s markets, the system implemented a conservative strategy, placing "no" bets on temperature ranges far from the predicted values. This reduced risk and increased the likelihood of accurate trades, resulting in a 20% profit over one week.

---

## Results
- **Profitability**: The automated trading system achieved a 20% profit in one week, demonstrating the effectiveness of the weather forecasting model and trading strategy.
- **Scalability**: The system can be scaled to additional weather variables or geographic regions, allowing for broader participation in prediction markets.


---

## Challenges & Future Improvements
- **Data Delays**: Occasional delays in data updates, especially from NCEI after weekends and holidays, impacted trading accuracy. Adjusting the strategy to rely less on recent predictions during these periods mitigated this issue.
- **Prediction Accuracy**: Given the strict one-degree temperature range, prediction errors were reduced by placing conservative "no" bets on less likely temperature ranges.
- **Data Fusion**: Integrating additional real-time data sources, such as satellite imagery, could improve the model's robustness.
- **Data Pipeline**: Can build a more optimized data pipeline if having access to paid weather API to improve the scalability and automation of the whole process.

---

## How to Use

1. **Install Dependencies**:
   Clone the repository and install the required Python packages:
   ```
   git clone https://github.com/yourrepo/weather-forecast-automated-trading.git
   pip install -r requirements.txt
   ```
2. **Configure API Keys**: Obtain an API key from Kalshi's platform and add it to the configuration file.
3. **Run the System**