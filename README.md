# Cross-Sectional Momentum Strategy  
### Factor-Based Equity Portfolio Construction

## Overview

This project implements a **cross-sectional momentum strategy** with full annotations explaining each modeling and portfolio construction step.

The objective is to:

- Rank assets cross-sectionally by momentum
- Construct long-short portfolios
- Evaluate performance stability
- Analyze turnover and transaction costs
- Understand factor-driven return decomposition

This notebook emphasizes clarity of implementation and economic intuition.

---

## Strategy Logic

Cross-sectional momentum exploits relative performance differences between assets.

At each rebalance date:

1. Compute trailing returns over a lookback window
2. Rank assets cross-sectionally
3. Long top quantile
4. Short bottom quantile
5. Rebalance periodically

---

## Signal Construction

### Momentum Factor

Momentum signal:

\[
M_i = \frac{P_{t}}{P_{t-L}} - 1
\]

Where:

- \( L \) = Lookback window  
- \( P_t \) = Current price  
- \( P_{t-L} \) = Historical price  

Signals are ranked cross-sectionally.

---

## Portfolio Construction

### Long-Short Portfolio

- Long: Top decile (or quintile)
- Short: Bottom decile (or quintile)
- Equal weight within each side
- Dollar-neutral structure

Portfolio return:

\[
R_t = \frac{1}{N_L}\sum_{i \in Long} r_{i,t}
-
\frac{1}{N_S}\sum_{i \in Short} r_{i,t}
\]

---

## Risk Management

The framework evaluates:

- Volatility of long-short spread
- Maximum drawdown
- Rolling Sharpe ratio
- Turnover and trading intensity

Optional extensions include:

- Volatility scaling
- Beta-neutral adjustment
- Sector-neutral ranking
- Liquidity filtering

---

## Backtesting Framework

- Rolling formation period
- Out-of-sample evaluation
- Rebalancing frequency control
- Transaction cost deduction
- Cumulative NAV tracking

Performance metrics include:

- Annualized return
- Annualized volatility
- Sharpe ratio
- Information ratio
- Hit ratio

---

## Factor Interpretation

This strategy captures:

- Behavioral underreaction
- Trend persistence
- Institutional flow continuation

The long-short structure isolates relative strength rather than market direction.

---

## Extensions

Possible enhancements:

- Multi-factor stacking (Value + Momentum)
- Residual momentum (beta-neutralized)
- Volatility-adjusted position sizing
- Cross-asset implementation
- Regime-dependent exposure

---

## Educational Value

This notebook demonstrates:

- Clean cross-sectional ranking implementation
- Portfolio construction mechanics
- Quantitative performance evaluation
- Factor investing intuition

---

## Disclaimer

For research and educational purposes only.  
Not investment advice.
