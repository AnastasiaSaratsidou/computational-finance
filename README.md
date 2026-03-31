# Computational Finance Workspace

This repository contains tools, notebooks, and packages for exploring numerical methods and financial models, with a focus on derivatives valuation. The goal is to provide a hands-on environment for experimenting, learning, and analyzing financial models.

---

## Option Valuation

This notebook demonstrates option pricing and hedging using Python. It covers:

- **Black-Scholes Model**: Analytical pricing of European options with delta calculation.  
- **Binomial Tree Model**: European and American option pricing via backward induction, with convergence and delta comparisons.  
- **Delta Hedging Simulation**: Euler-Maruyama simulation of stock paths, discrete hedging, and analysis of hedging errors under different frequencies and volatility mismatches.  

---

## Monte Carlo Sensitivity Analysis

Pricing European and Asian options via Monte Carlo simulation and studying Greek estimation under a GBM model. It covers:

- **Plain Monte Carlo**: European put pricing with convergence analysis and Black–Scholes comparison.
- **Bump-and-Revalue**: Finite difference delta estimation using independent vs. common random numbers, including bias–variance trade-off analysis.
- **Pathwise & Likelihood Ratio Methods**: Greek estimation for digital options, with logistic smoothing and MSE-based parameter tuning to handle payoff discontinuities.
- **Variance Reduction**: Control variate method for Asian options using the geometric average, achieving variance reduction by factor $(1 − \rho^2)$.

---

## Advanced Option Pricing

Pricing European call options numerically across ITM, ATM, and OTM moneyness cases using two complementary approaches:

- **Finite Difference PDE Solver**: Solves the Black–Scholes PDE in log-price space via FTCS and Crank–Nicolson schemes, with spatial convergence $\mathcal{O}(N^{-2})$ and delta estimation.
- **Fourier COS Method**: Recovers option prices directly from the GBM characteristic function via cosine expansions, achieving exponential convergence $\mathcal{O}(e^{-\alpha N})$ - significantly faster than grid-based methods.

---

> **Future Enhancements**  
> - Add configurable variables to interactively adjust model parameters and experiment with results.  
> - Expand documentation with detailed explanations, calculations, and references.