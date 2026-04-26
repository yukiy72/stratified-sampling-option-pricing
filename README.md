# Option Pricing using Stratified Sampling (Monte Carlo Simulation)

The content of this notebook is based on Chapter 4 of the book "Monte Carlo Methods in Financial Engineering" by Paul Glasserman. <br>

## Overview

This project implements a Monte Carlo simulation for pricing a European call option under the Geometric Brownian Motion (GBM) model.

To improve the efficiency and accuracy of standard Monte Carlo estimation, the project applies **stratified sampling** as a variance reduction technique.

The goal is to compare the performance (variance and convergence speed) between standard Monte Carlo and stratified sampling.

---

## Model Assumption

The underlying stock price follows a Geometric Brownian Motion (GBM):

$$\frac{dS(t)}{S(t)} = r dt + \sigma dW(t)$$

where:
- $S(t)$: stock price at time t  
- $r$: risk-free interest rate  
- $\sigma$: volatility  
- $W(t)$: Wiener process

---

## Option Type

- European Call Option
- Payoff: max(S(T) - K, 0)

---

## Method

### Standard Monte Carlo
- Simulate the path of stock prices $S(t)$ using GBM
- Compute discounted payoff
- Take average over all paths

### Stratified Sampling
- Construct strata based on the terminal value of the Wiener process
- Sample from each stratum
- Draw the whole path of the Wiener process by Brownian bridge construction
- Compute discounted payoff
- Compute the estimator and confidence interval

---

## Features

- GBM-based stock price simulation
- European call option pricing
- Standard Monte Carlo estimator
- Stratified sampling implementation
- Brownian bridge construction
- Confidence interval comparison between methods

---

## Usage

- The variable strata_info can be modified as needed. Its default value is:
```
strata_info = [
    [(0, 0.5), 30],
    [(0.5, 0.6), 50],
    [(0.6, 0.7), 50],
    [(0.7, 0.8), 50],
    [(0.8, 0.9), 50],
    [(0.9, 1.0), 50]
]
```
This specification divides the distribution of the Wiener process at terminal time $W(T)$ (i.e., N(0,T)) according to quantiles of its cumulative distribution function $\Phi_T(\cdot) = \Phi(\cdot/ \sqrt{T})$.
In particular, the first stratum corresponds to

$$ (\Phi^{-1}_T(0), \Phi^{-1}_T(0.5)) = (- \infty, 0), $$

and we generate 30 Wiener process sample paths whose terminal values fall within this interval.
Similarly, the second stratum corresponds to

$$ (\Phi^{-1}_T(0.5), \Phi^{-1}_T(0.6)) = (0, \Phi(0.6) \sqrt{T}) = (0, \ 0.2533 \sqrt{T})$$

and we generate 50 sample paths whose terminal values lie in this interval. The same procedure is applied to the remaining strata, with the specified number of samples generated in each case.

You can modify both the construction of the strata and the number of samples. For example, you may set this variable to:
```
strata_info = [
    [(0, 0.25), 100],
    [(0.25, 0.5), 100],
    [(0.5, 0.75), 100],
    [(0.75, 1.0), 100]
]
```

---

## Tech Stack

- Python
- NumPy

---

## Results

Stratified sampling shows:
- Lower variance (i.e., narrower confidence interval) compared to standard Monte Carlo

---

## References

1. Glasserman, P. (2003) *Monte Carlo Methods in Financial Engineering*. Springer, New York.

---
