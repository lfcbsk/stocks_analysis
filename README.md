# Vietnam Stock Market Investment Analytics

## 1. Project Overview

This project analyzes Vietnam large-cap stock market data using Python and Power BI.

The main objective is not to predict future stock prices, but to understand historical market behavior through performance, risk, liquidity, sector, benchmark, and portfolio analysis.

The project focuses on answering investment-oriented questions such as:

- Which stocks delivered the strongest historical returns?
- Did high-return stocks also carry higher downside risk?
- Which stocks showed better risk-adjusted performance?
- How sensitive were individual stocks to VNINDEX?
- Which sectors had stronger or weaker performance?
- Can simple portfolio strategies outperform the market benchmark?

The final output includes:

- A Python EDA notebook for statistical and financial analysis.
- A Power BI dashboard for interactive market insight and storytelling.
- Processed datasets ready for dashboard visualization.

---

## 2. Business Problem

Investors often look only at stock price movements or total return. However, return alone does not provide a complete picture of investment quality.

A stock may generate high return but also experience:

- High volatility
- Deep drawdown
- Strong dependence on market movements
- Weak liquidity
- High sector concentration risk

This project builds a data-driven investment analytics workflow to evaluate stocks from multiple perspectives:

1. Return performance
2. Risk and downside exposure
3. Risk-adjusted return
4. Market sensitivity
5. Sector behavior
6. Portfolio trade-offs

The analysis aims to support better investment decision-making by combining financial metrics with interactive dashboard reporting.

---

## 3. Dataset

The project uses historical daily OHLCV stock data for Vietnamese large-cap stocks and VNINDEX as the market benchmark from Kaggle (![Link](https://www.kaggle.com/datasets/bolongv/stock-prices-vn30-index-vietnam-82025?utm_source=chatgpt.com).

### Raw Data

Raw stock files are stored in:

```text
vn30_dataset/
```

Each stock CSV contains daily market data with columns such as:

```text
time, open, high, low, close, volume, symbol
```

VNINDEX data is stored separately as:

```text
VNINDEX.csv
```

### Cleaned Data

The cleaned and combined dataset is stored in:

```text
processed_data/clean_full.csv
```

Main columns:

| Column | Description |
|---|---|
| date | Trading date |
| ticker | Stock ticker or VNINDEX |
| open | Opening price |
| high | Highest price |
| low | Lowest price |
| close | Closing price |
| volume | Trading volume |
| data_quality | Data coverage quality flag |

The dataset covers the period from **03/08/2020 to 01/08/2025** and includes **29 stocks plus VNINDEX**.

---

## 4. Project Structure

```text
stocks_analysis/
│
├── vn30_dataset/
│   ├── ACB.csv
│   ├── BCM.csv
│   ├── BID.csv
│   ├── ...
│   └── VRE.csv
│
├── processed_data/
│   ├── clean_full.csv
│   │
│   └── powerbi/
│       ├── beta_metrics.csv
│       ├── fact_cumulative_returns.csv
│       ├── fact_daily_returns.csv
│       ├── fact_drawdown.csv
│       ├── fact_prices.csv
│       ├── portfolio_cumulative_returns.csv
│       ├── portfolio_metrics.csv
│       ├── risk_metrics.csv
│       └── sector_metrics.csv
│
├── process_data.ipynb
├── EDA.ipynb
├── VNINDEX.csv
├── visualize.pbix
├── LICENSE
└── README.md
```

---

## 5. Tools and Technologies

### Programming and Analysis

- Python
- Pandas
- NumPy
- Plotly
- Matplotlib
- Seaborn

### Financial Analytics

- Daily return
- Log return
- Cumulative return
- Annualized return
- Annualized volatility
- Sharpe ratio
- Max drawdown
- Value at Risk
- Conditional Value at Risk
- Beta against VNINDEX
- Correlation analysis
- Portfolio simulation

### Dashboard

- Power BI
- DAX measures
- Interactive slicers
- Multi-page dashboard design

---

## 6. Analysis Workflow

The project is divided into two main parts.

---

## Part 1: Data Processing

Notebook:

```text
process_data.ipynb
```

Main tasks:

1. Load individual stock CSV files.
2. Standardize column names.
3. Convert date columns to proper datetime format.
4. Combine all tickers into one long-format dataset.
5. Add VNINDEX as the benchmark index.
6. Check missing values, duplicate rows, and data coverage.
7. Create a clean full dataset for analysis.

Output:

```text
processed_data/clean_full.csv
```

---

## Part 2: Exploratory Data Analysis and Financial Analysis

Notebook:

```text
EDA.ipynb
```

Main analysis sections:

1. Data quality audit
2. Descriptive statistics
3. Price and volume analysis
4. Daily return distribution
5. Outlier and extreme movement analysis
6. Total return analysis
7. Risk metrics
8. Beta analysis against VNINDEX
9. Correlation analysis
10. Sector-level comparison
11. Portfolio simulation
12. Export tables for Power BI

---

## 7. Key Metrics

### Return Metrics

| Metric | Description |
|---|---|
| Daily return | Daily percentage price change |
| Log return | Logarithmic return for statistical analysis |
| Cumulative return | Total compounded return over time |
| Total return | Return from start date to end date |
| Annualized return | Daily return annualized using 252 trading days |

### Risk Metrics

| Metric | Description |
|---|---|
| Annualized volatility | Standard deviation of daily returns annualized |
| Sharpe ratio | Return per unit of volatility |
| Max drawdown | Largest peak-to-trough decline |
| VaR 95% | Estimated loss threshold at 95% confidence |
| CVaR 95% | Average loss beyond the VaR threshold |

### Market Sensitivity Metrics

| Metric | Description |
|---|---|
| Beta | Sensitivity of stock return to VNINDEX return |
| Correlation | Co-movement between stock returns |
| Outperformance rate | Frequency of stock return exceeding benchmark return |

---

## 8. Power BI Dashboard

Dashboard file:

```text
visualize.pbix
```

The Power BI dashboard is designed to communicate the analysis results through an interactive investment dashboard.

---

### Page 1: Market Overview

Purpose:

Provide a high-level overview of the market, benchmark performance, stock universe, and top-performing stocks.

Main components:

- Date range
- Number of stocks
- Trading days
- Latest VNINDEX close
- VNINDEX total return
- Latest market volume
- Average daily market volume
- VNINDEX close price trend
- Top stocks by total return
- Selected stock price trend

Key insight:

VNINDEX shows a full market cycle from the 2021 bull market to the 2022 correction and later recovery. Stock performance is highly dispersed, which suggests that ticker selection played an important role during the period.

---

### Page 2: Stock Screener

Purpose:

Allow users to compare stocks based on return, risk, and risk-adjusted performance.

Main components:

- Ticker slicer
- Sector slicer
- Stock ranking table
- Total return
- Annualized return
- Annualized volatility
- Sharpe ratio
- Max drawdown
- VaR and CVaR
- Beta

Key insight:

A stock with high return is not always the best investment candidate. Risk-adjusted metrics such as Sharpe ratio and drawdown provide a more balanced view of performance quality.

---

### Page 3: Risk and Return Analysis

Purpose:

Visualize the trade-off between return and risk across stocks.

Main components:

- Risk-return scatter plot
- Annualized return ranking
- Volatility ranking
- Sharpe ratio ranking
- Max drawdown ranking
- Beta comparison

Key insight:

Stocks in the upper-left area of the risk-return chart are more attractive because they provide higher return with lower volatility. High-beta and high-volatility stocks may perform well during bull markets but can suffer larger losses during corrections.

---

### Page 4: Sector and Portfolio Insights

Purpose:

Analyze sector-level behavior and compare simple portfolio strategies.

Main components:

- Average return by sector
- Average volatility by sector
- Average Sharpe ratio by sector
- Sector drawdown comparison
- Portfolio cumulative return
- Portfolio risk-return metrics
- Portfolio drawdown comparison

Portfolio strategies:

| Portfolio | Description |
|---|---|
| Equal Weight | Allocates equally across selected stocks |
| Top 5 Sharpe | Selects stocks with the highest Sharpe ratio |
| Low Volatility | Selects stocks with the lowest volatility |
| VNINDEX | Market benchmark |

Key insight:

Simple portfolio strategies show different trade-offs. A Top Sharpe portfolio may deliver stronger risk-adjusted return, while a Low Volatility portfolio focuses more on downside protection.

---

## 9. Dashboard Preview

Add dashboard screenshots to the `preview_of_PowerBI/` folder and update the paths below.

### Market Overview

```text
images/market_overview.png
```

![Market Overview](preview_of_PowerBI/Screenshot%202026-07-06%20195822.png)

### Stock Screener

```text
images/stock_screener.png
```

![Stock Screener](preview_of_PowerBI/Screenshot%202026-07-06%20195840.png)

### Risk and Return Analysis

```text
images/risk_return_analysis.png
```

![Risk and Return Analysis](preview_of_PowerBI/Screenshot%202026-07-06%20195840.png)

### Sector and Portfolio Insights

```text
images/sector_portfolio_insights.png
```

![Sector and Portfolio Insights](preview_of_PowerBI/Screenshot%202026-07-06%20195855.png)

---

## 10. Main Findings

### 1. Strong performance dispersion across stocks

The analysis shows large differences in total return across tickers. Some stocks significantly outperformed the market, while others generated weak or negative returns.

This means stock selection was very important during the sample period.

---

### 2. High return often comes with high risk

Several high-return stocks also experienced large volatility and deep drawdowns. Therefore, ranking stocks only by total return can be misleading.

Risk metrics such as max drawdown, volatility, VaR, and CVaR provide a more complete investment view.

---

### 3. Risk-adjusted performance gives better insight

Sharpe ratio helps compare stocks based on return per unit of risk. Some stocks may not have the highest raw return but still provide more efficient performance after adjusting for volatility.

---

### 4. Market sensitivity differs across tickers

Beta analysis shows that some stocks are more sensitive to VNINDEX movements. High-beta stocks can benefit more during market rallies but may decline more sharply during market corrections.

---

### 5. Sector behavior is uneven

Different sectors show different return and risk profiles. Banking, securities, real estate, consumer, energy, and technology-related stocks behave differently across market regimes.

Sector allocation is therefore an important part of portfolio construction.

---

### 6. Portfolio construction improves decision-making

Simple portfolio simulations show that different allocation rules lead to different outcomes.

- Equal-weight allocation provides a simple diversification benchmark.
- Top Sharpe selection focuses on risk-adjusted return.
- Low Volatility selection focuses on downside protection.
- VNINDEX is used as the market benchmark.

---

## 11. Methodology

### Return Calculation

Simple daily return:

```text
R_t = P_t / P_{t-1} - 1
```

Cumulative return:

```text
Cumulative Return = (1 + R_1) × (1 + R_2) × ... × (1 + R_t) - 1
```

---

### Annualized Return

```text
Annualized Return = Mean Daily Return × 252
```

---

### Annualized Volatility

```text
Annualized Volatility = Daily Return Standard Deviation × sqrt(252)
```

---

### Sharpe Ratio

```text
Sharpe Ratio = Annualized Return / Annualized Volatility
```

Note: The current version assumes a zero risk-free rate for simplicity.

---

### Max Drawdown

```text
Drawdown = Current Portfolio Value / Historical Peak Value - 1
```

Max drawdown is the most negative drawdown value.

---

### Beta

```text
Beta = Covariance(Stock Return, Market Return) / Variance(Market Return)
```

VNINDEX is used as the market benchmark.

---

## 12. Dashboard Design Logic

The dashboard follows an investment analysis flow:

```text
Market Overview
      ↓
Stock Screener
      ↓
Risk & Return Analysis
      ↓
Sector & Portfolio Insights
```

This structure allows users to move from general market understanding to specific stock comparison and finally to portfolio-level decision support.

---

## 13. Limitations

This project is for educational and analytical purposes only. It is not financial advice.

Main limitations:

- The analysis is based on historical data only.
- Past performance does not guarantee future returns.
- Transaction costs, taxes, slippage, and liquidity constraints are not included.
- Dividends, stock splits, and corporate actions may not be fully adjusted.
- The analysis mainly uses price and volume data.
- Fundamental data such as revenue, earnings, valuation, ROE, debt, and cash flow is not included.
- Sector analysis may be limited because some sectors have only a few representative stocks.

---

## 14. Project Summary

This project provides a complete investment analytics workflow for Vietnam large-cap stocks. It combines Python-based statistical and financial analysis with an interactive Power BI dashboard.

The project shows how historical stock market data can be transformed into actionable insights about performance, risk, market sensitivity, sector behavior, and portfolio trade-offs.
