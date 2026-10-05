# Stock Portfolio Optimization

A quantitative analysis of a diversified equity portfolio using statistical analysis, Principal Component Analysis (PCA), and Markowitz mean-variance optimization.

## Overview

This project analyzes a diversified portfolio of 11 stocks across five sectors using historical daily adjusted closing prices from January 2018 to January 2024.

The analysis covers:

- Log return analysis
- Annualized return and volatility
- Return distributions
- Correlation and covariance analysis
- Rolling volatility
- Sharpe ratio analysis
- Principal Component Analysis (PCA)
- PCA factor modelling
- Mean variance portfolio optimization
- Efficient frontier construction
- Minimum-variance portfolio
- Maximum-Sharpe portfolio
- Comparison of PCA based and full covariance optimization

The main objective is to investigate the relationship between risk, return and diversification, and to examine whether a lower-dimensional PCA factor model can approximate the full covariance structure of the portfolio.

---

## Portfolio

The analysis uses 11 stocks across five sectors:

| Sector | Stocks |
|---|---|
| Technology | AAPL, MSFT, GOOGL |
| Banking | JPM, BAC |
| Energy | XOM, CVX |
| Healthcare | JNJ, PFE |
| Indian IT | TCS.NS, INFY.NS |

Historical adjusted closing prices were obtained using the `yfinance` library.

The sample contains 1,318 daily observations covering January 2018 to January 2024.

---

## Methodology

### 1. Log Returns

Daily log returns are calculated as:

$$
r_t = \ln\left(\frac{P_t}{P_{t-1}}\right)
$$

Log returns are then used for the subsequent risk and portfolio analysis.

### 2. Risk and Return Analysis

The project calculates:

- Annualized expected returns
- Annualized volatility
- Sharpe ratios
- Rolling 30-day annualized volatility

A standard 252-trading-day annualization factor is used.

### 3. Correlation and Covariance

Covariance and correlation matrices are calculated to examine relationships between assets and identify diversification opportunities.

Some strong relationships observed in the dataset include:

- BAC–JPM: 0.91
- CVX–XOM: 0.85
- GOOGL–MSFT: 0.78
- AAPL–MSFT: 0.75
- INFY.NS–TCS.NS: approximately 0.65

The analysis also shows that healthcare stocks have relatively weaker correlations with much of the rest of the portfolio.

### 4. Principal Component Analysis

PCA is applied to the covariance matrix to identify the major factors driving portfolio risk.

The first principal component explains 49.3% of total variance.

The first two components explain 64.2%, while the first three explain 74.6%.

The factor loadings provide an interpretable view of the major sources of systematic movement across the assets.

### 5. Mean-Variance Optimization

The project applies the Markowitz mean-variance framework to construct portfolios along the efficient frontier.

The optimization considers:

- Expected returns
- Covariance between assets
- Portfolio variance
- Target returns
- Portfolio weights

Two key portfolios are examined:

**Minimum-variance portfolio**

- Annualized return: 12.66%
- Annualized volatility: 15.10%
- Sharpe ratio: 0.838

**Maximum-Sharpe portfolio**

- Annualized return: 38.57%
- Annualized volatility: 26.36%
- Sharpe ratio: 1.463

### 6. PCA Factor Model

The PCA covariance approximation is compared with the full covariance model.

Cumulative explained variance:

| Number of factors | Explained variance |
|---|---:|
| 1 | 49.3% |
| 2 | 64.2% |
| 3 | 74.6% |
| 4 | 81.4% |
| 5 | 87.4% |

The efficient frontier produced using five PCA factors is visually very close to the full-covariance frontier.

---

## Key Results

### Diversification

The minimum-variance portfolio achieves 15.10% annualized volatility, which is lower than the volatility of every individual asset in the dataset.

### Risk-adjusted performance

The maximum-Sharpe portfolio achieves a Sharpe ratio of 1.463, compared with 0.995 for the best individual asset in the dataset.

### PCA

Three principal components explain 74.6% of the covariance structure, while five components explain 87.4%.

The five-factor model produces an efficient frontier that is very close to the full-covariance result.

### Portfolio weights

The minimum-variance portfolio places substantial weights on JNJ, TCS.NS and XOM while using short positions in CVX and BAC under the unconstrained optimization.

The maximum-Sharpe portfolio has large long positions in XOM, INFY.NS and MSFT, alongside positions in JPM and TCS.NS.

---

## Visualizations

The project includes visualizations of:

- Normalized stock price trends
- Daily return distributions
- Risk-return profiles
- Correlation matrix
- Rolling volatility
- Sharpe ratios
- Covariance matrix
- PCA factor loadings
- PCA covariance reconstruction
- Efficient frontier
- Optimal portfolio weights
- PCA vs. full-covariance efficient frontiers

---

## Practical Limitations

The analysis has several limitations:

1. Expected returns are estimated from historical data and are therefore subject to estimation error.
2. Volatility is time-varying and can increase substantially during periods of market stress.
3. Return distributions show heavier tails than a normal distribution.
4. The unconstrained optimization can produce large short positions that may not be practical for real-world implementation.

Possible extensions include shrinkage covariance estimators, long-only constraints, scenario-based risk measures and Conditional Value at Risk (CVaR).

---

## Tools and Technologies

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- SciPy
- Scikit-learn
- yfinance
- Jupyter Notebook

