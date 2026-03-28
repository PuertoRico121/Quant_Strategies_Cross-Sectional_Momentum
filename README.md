# Cross-Sectional Equity Strategy (Annotated Implementation)

## Overview

This project implements a cross-sectional equity trading strategy based on ranking and relative performance across assets.

The objective is to:

- Construct cross-sectional signals
- Rank assets by factor scores
- Form long–short portfolios
- Evaluate performance with realistic backtesting assumptions
- Understand implementation details through annotated code

Unlike time-series momentum, which evaluates each asset independently, this framework compares assets against one another at each rebalance date.

---

## Strategy Logic

At each rebalance date:

1. Compute factor scores for all assets
2. Rank assets cross-sectionally
3. Select top quantile for long positions
4. Select bottom quantile for short positions
5. Rebalance portfolio weights

Cross-sectional ranking removes common market drift and isolates relative strength.

---

## Signal Construction

Typical factors include:

- Momentum (past N-day return)
- Volatility-adjusted return
- Rolling Sharpe ratio
- Mean-reversion score
- Relative strength indicator

Signals are standardized before ranking to ensure comparability across assets.

Standardization example:

z_score_i = (signal_i - cross_section_mean) / cross_section_std

---

## Portfolio Formation

### Long–Short Construction

- Equal weight within long basket
- Equal weight within short basket
- Dollar-neutral structure

If there are L long assets and S short assets:

weight_long_i  =  1 / L  
weight_short_i = -1 / S  

Total portfolio weight sums to zero.

---

## Portfolio Return Calculation

Portfolio return at time t:

R_portfolio_t = sum over i of ( weight_i at time t-1 * return_i at time t )

This ensures no look-ahead bias.

In expanded form:

R_portfolio_t = w_1,t-1 * R_1,t  
              + w_2,t-1 * R_2,t  
              + ...  
              + w_n,t-1 * R_n,t  

---

## Performance Metrics

Annualized Return:

Annual_Return = mean(daily_returns) * 252

Annualized Volatility:

Annual_Volatility = std(daily_returns) * sqrt(252)

Sharpe Ratio:

Sharpe = Annual_Return / Annual_Volatility

Maximum Drawdown:

Drawdown_t = (Peak_NAV - NAV_t) / Peak_NAV

---

## Backtesting Considerations

The implementation includes:

- Signal shifting to prevent look-ahead bias
- Rolling ranking
- Position rebalancing
- Transaction cost modeling
- Turnover tracking

Turnover at time t:

Turnover_t = sum over i of abs(weight_i,t - weight_i,t-1)

---

## Extensions

This framework can be extended to:

- Multi-factor composite ranking
- Sector-neutral portfolio construction
- Beta-neutral adjustment
- Volatility targeting overlay
- Machine learning cross-sectional scoring

---

## Applications

Cross-sectional strategies are widely used in:

- Equity market-neutral funds
- Statistical arbitrage
- Factor investing portfolios
- Long–short hedge fund strategies

---

## Disclaimer

This project is for research and educational purposes only.  
It does not constitute investment advice.
