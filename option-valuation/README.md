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
| **2.1** | Binomial Tree valuation |
| **2.2** | Comparison of BT vs Black-Scholes across volatilities |
| **2.3** | Convergence study (BT → BS as N → ∞) |
| **2.4** | Delta comparison (BT vs BS) |
| **3.1** | American options with early exercise |
| **4.1** | Delta hedging simulation using Euler scheme |

## Usage

```bash
# Install dependencies
uv sync

# Launch Jupyter and open the notebook
cd option-valuation
uv run jupyter notebook option_valuation.ipynb
```

Or execute non-interactively:

```bash
uv run jupyter nbconvert --to notebook --execute option-valuation/option_valuation.ipynb --ExecutePreprocessor.timeout=600 --output executed_option_valuation.ipynb
```

## Structure

```
option_valuation/
├── option_valuation.ipynb   # Main notebook
└── README.md
```