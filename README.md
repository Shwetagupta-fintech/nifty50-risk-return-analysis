# Nifty 50 Risk & Return Analysis (2019–2025)

*Question:* Over seven years that include the COVID-19 crash, which large Indian stocks actually rewarded investors for the risk they took?

## Data
- Daily closing prices, Jan 2019 – Dec 2025, for the Nifty 50 index and 10 large stocks across [sectors]
- Source: [Yahoo Finance via yfinance]
- Risk-free rate: [x]% (Indian 10-year government bond)

## Method
- Annualised return (CAGR) and volatility
- Sharpe ratio, maximum drawdown
- Beta vs Nifty 50 (linear regression)
- Correlation across sectors
- Equal-weight portfolio vs the index
- COVID-19 crash and recovery (2020)

## Key findings
1. *Hindustan Unilever returned 5.50% a year, below the risk-free rate.* A "safe" blue-chip didn't pay for its risk.
2. [Best risk-adjusted stock: name, Sharpe ratio]
3. [Equal-weight portfolio vs Nifty 50: which did better, by how much]
4. [COVID crash: max drawdown, and how long the recovery took]



![Cumulative returns](images/cumulative_returns.png)




![Risk vs return](images/risk_vs_return.png)




![Correlation heatmap](images/correlation_heatmap.png)



## Limitations
- *Survivorship bias:* I picked today's large companies, so the sample leaves out firms that fell out of the index. Returns are likely overstated.
- Prices only; dividends not included (affects high-dividend stocks such as HUL).
- [any other limitation she documented]

## How to run
1. Open [notebook name].ipynb in Google Colab
2. Run all cells (packages listed in requirements.txt)

## Tools
Python · pandas · NumPy · matplotlib · seaborn · Google Colab

## Author
Shweta Gupta · [LinkedIn](https://www.linkedin.com/in/shweta-gupta-fintech/)
