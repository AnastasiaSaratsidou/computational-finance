# Monte Carlo Sensitivity Analysis

This project covers Monte Carlo simulation for option pricing and Greek estimation using:

- **Plain Monte Carlo** for European put option pricing
- **Bump-and-Revalue** (finite difference) delta estimation
- **Pathwise and Likelihood Ratio** methods for digital option Greeks
- **Variance Reduction** via control variates for Asian options

## Problem Setup

European/Asian option on a non-dividend-paying stock:

- **Spot Price**: €100
- **Strike**: €99
- **Maturity**: 1 year
- **Risk-free rate**: 6%
- **Volatility**: 20%

## Notebooks

| Notebook | Description |
|----------|-------------|
| `monte_carlo_simulation.ipynb` | European put pricing, convergence and sensitivity analysis |
| `bump_and_revalue.ipynb` | Delta estimation for European and digital options |
| `variance_reduction.ipynb` | Control variate method for Asian option pricing |

---

### `monte_carlo_simulation.ipynb`

Prices a European put option via Monte Carlo and studies convergence and parameter sensitivity.

| Section | Description |
|---------|-------------|
| **1** | Monte Carlo simulation under GBM - $M$ paths, $N$ time steps |
| **2** | Comparison with Black–Scholes closed-form put price |
| **3** | Convergence analysis - MC estimator vs number of paths (SLLN) |
| **4** | Sensitivity to volatility $\sigma$ - asymptotic behaviour as $\sigma \to \infty$ |
| **5** | Sensitivity to strike $K$ - linear growth of put value with strike |
| **6** | Standard error and 95% confidence interval via CLT ($SE = s/\sqrt{M}$) |

---

### `bump_and_revalue.ipynb`

Estimates delta $\Delta = \partial V / \partial S_0$ using finite difference and pathwise methods.

| Section | Description |
|---------|-------------|
| **1** | Forward finite difference delta for European calls - independent vs common random numbers |
| **1.1** | Bias–variance trade-off as a function of bump size $h$ |
| **2** | Bump-and-revalue applied to digital options - failure due to payoff discontinuity |
| **2.1** | Logistic smoothing of the digital payoff - optimal $(\alpha, h)$ via MSE grid search |
| **2.2** | Pathwise delta estimator - differentiating inside the expectation |
| **2.3** | Likelihood ratio (score function) method - more stable than pathwise for discontinuous payoffs |

---

### `variance_reduction.ipynb`

Prices Asian options and reduces estimator variance using the geometric average as a control variate.

| Section | Description |
|---------|-------------|
| **1** | Analytical price for geometric Asian call - adjusted drift and volatility under BS |
| **2** | Monte Carlo simulation for geometric Asian option - convergence to analytical value |
| **3** | Arithmetic Asian option - no closed form, MC only |
| **4** | Control variate estimator $\hat{A}_{CV} = A - \beta^*(G - \mathbb{E}[G])$ - variance reduction by factor $(1 - \rho^2)$ |

## Usage

```bash
# Install dependencies
uv sync

# Launch Jupyter and open the notebooks
cd mc-sensitivity-analysis/notebooks
uv run jupyter notebook monte_carlo_simulation.ipynb
uv run jupyter notebook bump_and_revalue.ipynb
uv run jupyter notebook variance_reduction.ipynb
```

Or execute non-interactively:

```bash
uv run jupyter nbconvert --to notebook --execute notebooks/monte_carlo_simulation.ipynb --ExecutePreprocessor.timeout=600 --output executed_monte_carlo_simulation.ipynb
uv run jupyter nbconvert --to notebook --execute notebooks/bump_and_revalue.ipynb --ExecutePreprocessor.timeout=600 --output executed_bump_and_revalue.ipynb
uv run jupyter nbconvert --to notebook --execute notebooks/variance_reduction.ipynb --ExecutePreprocessor.timeout=600 --output executed_variance_reduction.ipynb
```

## Structure

```
mc-sensitivity-analysis/
├── notebooks/
│   ├── monte_carlo_simulation.ipynb   # European put pricing and sensitivity
│   ├── bump_and_revalue.ipynb         # Delta estimation methods
│   └── variance_reduction.ipynb       # Control variate for Asian options
└── README.md
```