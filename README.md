# Nifty 50 Risk & Return Analysis (2019–2025)

**Author:** Shweta Gupta · [LinkedIn](https://www.linkedin.com/in/shweta-gupta-fintech/)

An analysis of the return, risk and risk-adjusted performance of the Nifty 50 index and 10 large Indian stocks from different sectors over 2019–2025, including how they behaved during the COVID-19 crash.

> **Headline finding:** Hindustan Unilever, widely seen as a "safe" blue-chip, returned 5.50% a year, less than the 6.77% risk-free rate, while being more volatile than the Nifty 50.

## Objective

To answer three questions:
1. Which large Indian stocks rewarded investors for the risk they took?
2. How much protection did diversification give, on normal days and in a crash?
3. Which sectors fell most and recovered fastest during the COVID-19 crash of 2020?

## Data

- **Source:** Yahoo Finance, via the `yfinance` Python library
- **Period:** 2 January 2019 – 31 December 2025 (1,729 trading days)
- **Prices:** daily closing prices, adjusted for dividends and stock splits
- **Tickers:** Nifty 50 index (^NSEI) and 10 stocks from 8 sectors

| Stock | Sector |
|---|---|
| Reliance Industries | Energy |
| HDFC Bank | Banking |
| Infosys | IT |
| TCS | IT |
| ITC | FMCG |
| Hindustan Unilever | FMCG |
| Sun Pharma | Pharma |
| Maruti Suzuki | Auto |
| Larsen & Toubro | Infrastructure |
| Bharti Airtel | Telecom |

- **Risk-free rate:** 6.77%, the 2019–2025 average yield on India's 10-year government bond (source: FRED / OECD)

## Method

1. **Data cleaning:** forward-filled 2 gaps in the middle of the Nifty data and dropped the first row, which had no earlier price to fill from.
2. **Return:** Compound Annual Growth Rate (CAGR).
3. **Risk:** annualised volatility (standard deviation of daily returns × √252).
4. **Risk-adjusted return:** Sharpe ratio = (CAGR − risk-free rate) ÷ volatility.
5. **Maximum drawdown:** the largest fall from a previous peak to a low.
6. **Beta:** linear regression of each stock's daily returns against the Nifty 50's daily returns.
7. **Correlation:** pairwise correlation of daily returns across the 10 stocks.
8. **Equal-weight portfolio:** ₹10,000 invested in each stock on 2 January 2019 and held to the end of 2025, compared with ₹1,00,000 in the Nifty 50.
9. **COVID-19 crash:** fall from the pre-crash peak (January to mid-February 2020) to the low (February to April 2020), and the number of days to recover to the pre-crash peak.

## Key Findings

**1. Most stocks were not worth their extra risk.**
Only Bharti Airtel (Sharpe 0.95) and Sun Pharma (0.61) delivered strong risk-adjusted returns. The Nifty 50 (0.38) beat 6 of the 10 stocks on Sharpe.

![Risk vs return](images/risk_vs_return.png)

**2. "Safe" is not the same as low risk.**
Hindustan Unilever returned 5.50% a year, less than the 6.77% risk-free rate, so its Sharpe ratio was negative (−0.06). It was also more volatile than the Nifty (22.57% vs 17.56%).

**3. Diversification reduced everyday risk.**
The Nifty 50 had lower volatility (17.56%) than every individual stock. Stocks in the same sector were the most correlated (Infosys–TCS: 0.65), while most cross-sector pairs were between 0.20 and 0.35.

![Correlation heatmap](images/correlation_heatmap.png)

**4. Diversification protected less in a crash.**
8 of 11 tickers hit their worst fall in March–April 2020. The Nifty's maximum drawdown (−38.44%) ranked only 6th of 11, because most stocks fell together during the crash.

**5. A low beta does not mean low risk.**
ITC had a low beta (0.68) but still fell 51.11% from its peak and took 326 days to recover from the COVID low, the slowest of all 11 tickers. Its fall was driven by company-specific factors rather than the market.

**6. Defensive stocks mostly protected investors in the COVID crash.**
HUL fell the least (−19.80%) and recovered in 12 days. Sun Pharma fell 28.10% and recovered in 17 days. ITC was the exception among defensive stocks.

**7. The equal-weight portfolio beat the Nifty, with an important caveat.**

| | Equal-weight portfolio | Nifty 50 |
|---|---|---|
| CAGR | 17.54% | 13.47% |
| Volatility | 16.11% | 17.56% |
| Sharpe ratio | 0.67 | 0.38 |
| Maximum drawdown | −31.12% | −38.44% |
| Value of ₹1,00,000 | ₹3,09,629 | ₹2,42,109 |

![Growth of ₹1,00,000](images/cumulative_returns.png)

These results are inflated by survivorship bias (see Limitations).

## Limitations

- **Survivorship bias:** the 10 stocks were chosen in 2026, knowing they are large, successful companies today. A fair test would use the largest Nifty stocks as of January 2019, including any that later performed badly.
- **Simplified Sharpe ratio:** calculated using CAGR and a single average risk-free rate. The textbook version uses the average of daily excess returns.
- **Forward-filled data:** 2 missing Nifty values were forward-filled, creating 2 artificial 0% return days. The effect on results is negligible.
- **Small sample:** 10 stocks from 8 sectors do not represent the full Nifty 50.
- **No transaction costs or taxes:** real returns would be lower.
- **Buy-and-hold portfolio:** the equal-weight portfolio was not rebalanced, so its weights drifted over time.

## Tools

Python (pandas, NumPy, matplotlib, seaborn), yfinance, Google Colab

## How to Run

1. Open `Nifty50_Risk_Return_Analysis.ipynb` in Google Colab.
2. Click **Runtime → Run all**.

All data is downloaded automatically. No files or API keys are needed. Packages are listed in `requirements.txt`.
