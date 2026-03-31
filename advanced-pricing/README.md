# Advanced Option Pricing

This folder covers two numerical approaches for pricing European call options, progressing from grid-based PDE solvers to spectral methods.

## Problem Setup

European call option on a non-dividend-paying stock:

- **Strike**: €110
- **Maturity**: 1 year
- **Risk-free rate**: 4%
- **Volatility**: 30%
- **Moneyness**: ITM (S₀ = 100), ATM (S₀ = 110), OTM (S₀ = 120)

## Notebooks

| Notebook | Method | Description |
|----------|--------|-------------|
| `pde_fd_schemes.ipynb` | Finite Difference | Solves the Black–Scholes PDE in log-price space using FTCS and Crank–Nicolson schemes |
| `fourier_cos_method.ipynb` | Fourier COS | Prices options directly from the characteristic function via Fourier cosine expansions |

---

### `pde_fd_schemes.ipynb`

Transforms the Black–Scholes PDE into log-price space and solves it backward in time on a uniform grid.

| Section | Description |
|---------|-------------|
| **1** | Grid construction and PDE transformation ($X = \log S$, $\tau = T - t$) |
| **2** | FTCS explicit scheme - tridiagonal matrix $A$, coefficients $a_{-1}, a_0, a_1$ |
| **3** | Crank–Nicolson implicit scheme - system $BV^{n+1} = AV^n$, LU factorization |
| **4** | Boundary and terminal conditions |
| **5** | Numerical experiments - option prices vs Black–Scholes for all three moneyness cases |
| **6** | Convergence analysis - spatial order $\mathcal{O}(\Delta X^2) = \mathcal{O}(N^{-2})$ confirmed |
| **7** | Delta estimation - $\Delta = \partial V / \partial S$ compared against analytical Black–Scholes delta |

---

### `fourier_cos_method.ipynb`

Prices options by expanding the risk-neutral density in a Fourier cosine basis and recovering coefficients from the known characteristic function of GBM.

| Section | Description |
|---------|-------------|
| **1** | Problem formulation - log-return transformation, risk-neutral pricing integral |
| **2** | COS method derivation - Fourier cosine expansion, connection to characteristic function |
| **3** | Coefficient construction - analytical payoff coefficients $G_k$ via $\chi_k$, $\psi_k$ |
| **4** | Numerical implementation - domain truncation, assembly of the COS pricing formula |
| **5** | Experiments and validation - COS vs Black–Scholes for ITM, ATM, OTM |
| **6** | Convergence analysis - exponential $\mathcal{O}(e^{-\alpha N})$ decay, comparison with FD $\mathcal{O}(N^{-2})$ |

---

## Usage

```bash
# Install dependencies
uv sync

# Launch Jupyter
uv run jupyter notebook
```

Or execute non-interactively:

```bash
uv run jupyter nbconvert --to notebook --execute pde_fd_schemes.ipynb --ExecutePreprocessor.timeout=600 --output executed_pde_fd_schemes.ipynb
uv run jupyter nbconvert --to notebook --execute fourier_cos_method.ipynb --ExecutePreprocessor.timeout=600 --output executed_fourier_cos_method.ipynb
```

## Structure

```
advanced-pricing/
├── pde_fd_schemes.ipynb       # Finite difference PDE solver
├── fourier_cos_method.ipynb   # Fourier COS pricer
└── README.md
```