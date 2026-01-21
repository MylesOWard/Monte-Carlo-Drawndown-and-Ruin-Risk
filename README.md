# Monte Carlo Drawdown and Ruin Risk
### Capital Dynamics and Position Sizing Under Stochastic Returns

This repository is a small research toolkit for analysing **capital allocation, drawdown risk, and ruin probabilities** under repeated exposure to a stochastic return process with negative expected value.

Using Monte Carlo simulation, the project studies how different **position sizing and progression rules** affect bankroll dynamics, tail outcomes, and the likelihood of capital depletion. While the underlying model is intentionally simple, the framework is directly applicable to problems in **risk management, stress testing, and capital preservation**, where path dependence and extreme outcomes dominate long-run behaviour.

The code is designed to be easily modified, allowing parameters such as return distribution, edge, position sizing rules, and initial capital to be varied for scenario analysis.

The project is organised as reusable core logic in `src/` (random number generation, strategy implementations, simulation runner, and metrics) alongside a short notebook series that explains each strategy and visualises results.

---

## Project Overview

Many exposure-scaling or progression rules can appear attractive because they often produce frequent small gains. However, these same rules may embed **severe tail risk**, where rare adverse sequences lead to large drawdowns or total capital depletion.

This repository explores that trade-off by simulating different position sizing approaches under identical assumptions and measuring:

- **Ruin probability** (frequency of total capital depletion)
- **Final capital distributions** (skewness, tails, dispersion)
- **Mean vs median outcomes** (average vs typical realised results)
- **Path dependence and drawdown behaviour**

The emphasis is on understanding how **risk accumulates over time**, rather than on short-horizon performance.

---

## Position Sizing Rules Studied

| Rule | Description | Intuition | Primary Risk |
|:--|:--|:--|:--|
| **Constant position size** | Fixed exposure per iteration | Baseline reference model | Gradual capital decay under negative drift |
| **Exponential scaling** | Increase exposure after losses; reset after gains | Short-term variance suppression | Rare but catastrophic drawdowns |
| **Linear scaling** | Increment exposure after losses; decrement after gains | Smoother exposure adjustment | Persistent tail risk |

All rules are evaluated under identical return assumptions to isolate the effect of position sizing on risk and capital dynamics.

---

## Notebook Series

Each notebook combines narrative explanation with plots from both **single-path** simulations and **Monte Carlo** experiments.

| # | Notebook | Focus |
|:--|:--|:--|
| 01 | `01_constant_position_size.ipynb` | Baseline exposure rule, capital evolution, and outcome distributions |
| 02 | `02_exponential_position_scaling.ipynb` | Short-term gains vs tail risk and ruin behaviour |
| 03 | `03_linear_position_scaling.ipynb` | Linear adjustment rule and comparison of drawdown profiles |
| 04 | `04_strategy_comparison.ipynb` | Head-to-head Monte Carlo comparison of ruin rates and outcome distributions |

The final comparison notebook evaluates all strategies under identical parameters and summarises **ruin probability** and final-capital statistics.

---

## Repository Structure

- `notebooks/` — walkthrough notebooks (rule-by-rule analysis and final comparison)
- `src/` — reusable simulation code
  - `rng.py` — random number generation utilities
  - `runner.py` — Monte Carlo simulation runner
  - `metrics.py` — summary statistics and reporting helpers
  - `strategies/` — position sizing rule implementations
- `tests/` — unit tests for core logic (where applicable)

---

## Notes

Although inspired by classical probability problems, the focus of this project is on **risk management and capital preservation**, rather than recreational gambling or game-based analysis. The techniques demonstrated here are directly transferable to domains such as trading risk, portfolio stress testing, and scenario-based capital analysis.

