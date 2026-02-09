# Option Valuation

This project covers option pricing using:

- **Binomial Tree** methods (European & American options)
- **Black-Scholes** analytical formulas
- **Delta Hedging Simulation** using Euler-Maruyama discretization

## Problem Setup

European call option on a non-dividend-paying stock:
- **Spot Price**: €100
- **Strike**: €99 (OTM)
- **Maturity**: 1 year
- **Risk-free rate**: 6%
- **Volatility**: 20%

## Topics Covered

| Section | Description |
|---------|-------------|
| **B1** | Binomial Tree valuation |
| **B2** | Comparison of BT vs Black-Scholes across volatilities |
| **B3** | Convergence study (BT → BS as N → ∞) |
| **B4** | Delta comparison (BT vs BS) |
| **B5** | American options with early exercise |
| **C3** | Delta hedging simulation using Euler scheme |

## Usage

```bash
# Install dependencies
uv sync

# Run the notebook
uv run jupyter notebook option_valuation.ipynb
```

## Structure

```
option_valuation/
├── option_valuation.ipynb   # Main notebook
├── pyproject.toml           # Project config
└── README.md
```
