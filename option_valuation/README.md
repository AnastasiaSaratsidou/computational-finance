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

### Interactive (web UI)

```bash
# Install dependencies
uv sync

# Go to the project directory
cd option_valuation

# Start Jupyter and open the notebook in your browser
uv run jupyter notebook option_valuation.ipynb
```

### Headless / reproducible runs

```bash
# Execute the notebook non-interactively and save outputs
uv run jupyter nbconvert --to notebook --execute option_valuation.ipynb \
	--ExecutePreprocessor.timeout=600 --output executed_option_valuation.ipynb
```

Notes:
- The interactive command launches the web UI but does not auto-execute cells.
- Use the `nbconvert --execute` command for CI, batch runs, or to produce a finished
	notebook with cell outputs saved to `executed_option_valuation.ipynb`.

## Structure

```
option_valuation/
├── option_valuation.ipynb   # Main notebook
├── pyproject.toml           # Project config
└── README.md
```
