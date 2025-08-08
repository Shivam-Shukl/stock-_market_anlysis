# 📈 Stock Market Analysis & Monte Carlo Simulation

A comprehensive Python project for analyzing Google's stock performance and predicting future price movements using statistical modeling and Monte Carlo simulation.

## 📊 What This Project Does

This analysis performs **6 key financial functions** to help understand stock behavior and predict future performance:

### 1. **Historical Data Analysis**
- Fetches Google's (GOOG) stock data from Yahoo Finance
- Analyzes price trends, trading volume, and market patterns
- Provides statistical summary (mean, volatility, min/max prices)

### 2. **Technical Indicator Calculation**
- **10-day Moving Average**: Tracks short-term price momentum
- **20-day Moving Average**: Identifies medium-term trends  
- **50-day Moving Average**: Shows long-term market direction
- **Purpose**: Help identify buy/sell signals and trend reversals

### 3. **Daily Returns Analysis**
- Calculates day-to-day percentage price changes
- Creates return distribution histogram
- **Why Important**: Returns form the foundation for risk assessment and future predictions

### 4. **Risk Assessment (Value at Risk)**
```python
VaR_5% = returns.quantile(0.05)
# Result: "5% chance of losing more than X% in one day"
```
- Quantifies potential daily losses
- Helps investors understand downside risk before investing

### 5. **Monte Carlo Price Simulation**
The core prediction engine that:
- **Simulates 10,000 different price paths** for the next 365 days
- Uses historical volatility and average returns as inputs
- Generates realistic price scenarios based on past behavior

**How it works:**
1. Takes current stock price ($532.19)
2. Uses historical daily return patterns (mean: +0.05%, volatility: 2.1%)
3. Generates random daily returns following this pattern
4. Compounds these returns over 365 days
5. Repeats 10,000 times to create probability distribution

### 6. **Future Price Prediction & Confidence Intervals**
- **Expected Price**: Average of all 10,000 simulations
- **99% Confidence Interval**: Range where price will likely fall
- **Risk Scenarios**: Worst-case (1% probability) and best-case outcomes

## 🎯 Key Outputs & Interpretations

### Sample Results:
```
Current Price: $532.19
Expected Price (1 year): $580.45
99% Confidence Range: $425.80 - $756.32
Worst Case (1% chance): Below $425.80
Best Case (1% chance): Above $756.32
Daily VaR (5%): -3.2% (Risk of losing more than 3.2% in one day)
```

### What This Means:
- **For Investors**: "There's a 99% chance GOOG will be between $426-$756 next year"
- **Risk Management**: "5% chance of losing more than 3.2% on any given day"
- **Expected Return**: "+9.1% over the next year based on historical patterns"

## 🛠️ Technical Implementation

### Libraries Used:
- **pandas**: Data manipulation and analysis
- **numpy**: Mathematical calculations and random number generation
- **matplotlib/seaborn**: Data visualization
- **pandas-datareader**: Stock data fetching
- **datetime**: Date handling

### Core Functions:

#### Data Fetching:
```python
import pandas_datareader.data as pdr
data = pdr.get_data_yahoo('GOOG', start_date, end_date)
```

#### Moving Averages:
```python
data['MA10'] = data['Adj Close'].rolling(window=10).mean()
```

#### Monte Carlo Simulation:
```python
for simulation in range(10000):
    daily_returns = np.random.normal(mean_return, volatility, 365)
    price_path = simulate_price_path(current_price, daily_returns)
```

## 🚀 How to Run

### Prerequisites:
```bash
pip install pandas numpy matplotlib seaborn pandas-datareader
```

### Execution:
```bash
# Clone repository
git clone <your-repo-url>

# Navigate to directory  
cd stock-market-analysis

# Run analysis
python stock_analysis.py
```

## 📈 Generated Visualizations

1. **Historical Price Chart**: Shows actual price movement with moving averages
2. **Daily Returns Histogram**: Distribution of daily percentage changes
3. **Monte Carlo Simulation Paths**: 10,000 possible future price trajectories
4. **Final Price Distribution**: Probability distribution of where price might end up
5. **Risk vs Return Scatter Plot**: Visual risk assessment

## 🎓 Educational Value

### Financial Concepts Learned:
- **Volatility**: How much prices fluctuate (risk measurement)
- **Expected Return**: Average gain/loss over time
- **Value at Risk (VaR)**: Quantified downside risk
- **Monte Carlo Method**: Using randomness to solve deterministic problems
- **Technical Analysis**: Using price patterns for decision making

### Programming Skills Developed:
- Time series data handling
- Statistical analysis and visualization
- Random simulation techniques
- Financial data API usage
- Probability distribution analysis

## 🔍 Real-World Applications

- **Portfolio Management**: Assess risk before investing
- **Options Pricing**: Understand probability of price movements  
- **Risk Management**: Set stop-loss levels based on VaR
- **Investment Planning**: Set realistic return expectations
- **Trading Strategies**: Use moving averages for entry/exit signals

## ⚠️ Important Disclaimers

- **Not Financial Advice**: This is for educational purposes only
- **Past Performance**: Historical data doesn't guarantee future results
- **Market Complexity**: Real markets have factors not captured in this model
- **Model Limitations**: Assumes normal distribution of returns (may not always be true)

## 🔮 Future Enhancements

- Add multiple stock comparison
- Implement Sharpe ratio for risk-adjusted returns
- Include market sentiment analysis
- Add real-time data streaming
- Create interactive dashboard with Plotly
- Implement more sophisticated models (GARCH, Black-Scholes)

## 📄 License

MIT License - Feel free to use for educational and research purposes.
