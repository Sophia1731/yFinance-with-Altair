# Stock Analysis & Visualization Projects

This repository contains two comprehensive Python projects for stock market analysis, combining interactive visualizations and predictive modeling for major tech stocks.
Projects Overview
1. Stock Price Prediction with Statistical Models (StockPredStatModel1.pdf)

Advanced time series forecasting using multiple statistical and machine learning models to predict future stock prices.
2. Interactive Stock Visualizations with Altair (AltairVisStock1.pdf)

Rich, interactive dashboards for exploring stock performance, technical indicators, and market trends.
Features
Stock Price Prediction Models

    Simple Moving Average (SMA): Basic trend-following predictions
    Exponential Smoothing (Holt-Winters): Adaptive forecasting with trend and seasonality
    ARIMA: AutoRegressive Integrated Moving Average for time series
    Linear Regression: Multi-variable prediction using technical indicators
    Random Forest: Ensemble learning for capturing non-linear patterns

Technical Indicators:

    RSI (Relative Strength Index)
    MACD (Moving Average Convergence Divergence)
    Bollinger Bands
    Price Momentum (5, 10, 20 day)
    Volume ratios
    Lag features

Model Evaluation:

    RMSE (Root Mean Squared Error)
    MAE (Mean Absolute Error)
    MAPE (Mean Absolute Percentage Error)
    R² Score
    Comparative performance metrics

Interactive Visualizations

    Multi-Stock Comparison: Normalized price charts with hover interactions
    Brush & Zoom: Interactive selection for detailed analysis
    Metric Selector: Toggle between price, volume, volatility, and returns
    Click Highlighting: Focus on specific stocks
    Correlation Heatmap: Inter-stock relationships
    Candlestick Charts: OHLC data with Bollinger Bands
    Volume Profile: Price level trading activity
    Event Annotations: Mark significant market events
    Complete Dashboard: Combined multi-panel interface

Installation
Requirements
bash

pip install pandas numpy altair yfinance statsmodels scikit-learn

Detailed Dependencies
python

## Data manipulation
pandas>=1.5.0
numpy>=1.23.0

## Data fetching
yfinance>=0.2.0

## Visualization
altair>=5.0.0

## Statistical models
statsmodels>=0.14.0

## Machine learning
scikit-learn>=1.3.0

Usage
Stock Price Prediction
python

import pandas as pd
from stock_prediction import fetch_stock_data, run_complete_analysis

## Fetch historical data
tickers = ['AAPL', 'MSFT', 'GOOGL', 'AMZN', 'META']
stock_data = fetch_stock_data(tickers, period='2y')

## Run complete analysis
analysis = run_complete_analysis(stock_data, ticker='AAPL', test_size=0.2)

## View results
print(analysis['comparison'])  # Model performance comparison
analysis['prediction_chart']    # Actual vs predicted prices
analysis['error_chart']         # Prediction errors over time

Interactive Visualizations
python

from stock_viz import (
    fetch_stock_data, 
    create_stock_comparison,
    create_full_dashboard,
    create_candlestick_chart
)

## Fetch data
tickers = ['AAPL', 'MSFT', 'GOOGL', 'AMZN', 'META']
stock_data = fetch_stock_data(tickers, period='2y')

## Create visualizations
create_stock_comparison(stock_data)
create_full_dashboard(stock_data, default_ticker='AAPL')
create_candlestick_chart(stock_data, ticker='AAPL', days=90)


Key Functions:
Prediction Module

    fetch_stock_data()	Download historical stock data from Yahoo Finance
    prepare_prediction_data()	Engineer features and technical indicators
    split_train_test()	Time-series aware data splitting
    simple_moving_average_forecast()	SMA-based predictions
    exponential_smoothing_forecast()	Holt-Winters forecasting
    arima_forecast()	ARIMA model predictions
    linear_regression_forecast()	Multi-variable linear model
    random_forest_forecast()	Ensemble tree-based model
    evaluate_predictions()	Calculate error metrics
    compare_models()	Side-by-side model comparison
    
Visualization Module
    
    create_stock_comparison()	Multi-stock normalized performance
    create_brush_zoom_with_volume()	Interactive zoom with volume
    create_metric_selector()	Dropdown for different metrics
    create_click_comparison()	Click-to-highlight interface
    create_full_dashboard()	Comprehensive multi-panel view
    create_correlation_heatmap()	Inter-stock correlation matrix
    create_candlestick_chart()	OHLC with Bollinger Bands
    create_volume_profile()	Horizontal volume distribution
    create_annotated_performance()	Charts with event markers

    
Example Analysis Workflow
python

## 1. Fetch data
stock_data = fetch_stock_data(['AAPL', 'MSFT', 'GOOGL'], period='2y')

## 2. Visualize overall trends
create_stock_comparison(stock_data)

## 3. Detailed technical analysis
create_candlestick_chart(stock_data, ticker='AAPL', days=90)

## 4. Run predictions
analysis = run_complete_analysis(stock_data, ticker='AAPL')

## 5. Compare model performance
print(analysis['comparison'])

## 6. Visualize predictions
analysis['prediction_chart']
analysis['error_chart']

Model Performance Insights

The prediction module automatically compares all models and ranks them by RMSE. Typical findings:

    Random Forest often performs best for short-term predictions due to its ability to capture non-linear patterns
    Linear Regression provides interpretable coefficients showing feature importance
    ARIMA excels when clear autoregressive patterns exist
    Exponential Smoothing adapts well to trends and seasonality
    Moving Average serves as a baseline, though it lags actual prices

Technical Indicators Explained

    Moving Averages (MA): Smoothed price trends (20-day, 50-day)
    RSI: Momentum indicator (0-100, overbought/oversold signals)
    MACD: Trend-following momentum indicator
    Bollinger Bands: Volatility bands around moving average
    Volume Ratio: Trading activity relative to average
    Normalized Price: Percentage change from starting point

Limitations & Disclaimers

    Not Financial Advice: These tools are for educational and research purposes only
    Past Performance: Historical patterns do not guarantee future results
    Market Risk: Stock markets are influenced by countless unpredictable factors
    Model Assumptions: All models make simplifying assumptions about market behavior
    Data Quality: Results depend on data accuracy from Yahoo Finance

Customization
Adding New Stocks
python

tickers = ['AAPL', 'MSFT', 'TSLA', 'NVDA', 'AMD']
stock_data = fetch_stock_data(tickers, period='2y')

Adjusting Prediction Parameters
python

## Change train/test split
analysis = run_complete_analysis(stock_data, ticker='AAPL', test_size=0.3)

## Modify ARIMA parameters
arima_forecast(train, test, order=(7, 1, 2))

## Adjust Random Forest
model = RandomForestRegressor(n_estimators=200, max_depth=15)

Custom Event Annotations
python

events = [
    {'date': '2024-01-15', 'label': 'Product Launch'},
    {'date': '2024-06-01', 'label': 'Earnings Report'}
]
create_annotated_performance(stock_data, events=events)
