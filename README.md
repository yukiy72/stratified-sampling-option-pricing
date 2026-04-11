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
- Simulate terminal stock prices using GBM
- Compute discounted payoff
- Take average over all paths

### Stratified Sampling
- Construct strata based on the terminal value of the Wiener process
- Sample from each stratum
- Reduce variance compared to naive Monte Carlo

---

## Features

- GBM-based stock price simulation
- European call option pricing
- Standard Monte Carlo estimator
- Stratified sampling implementation
- Confidence interval comparison between methods

---

## Tech Stack

- Python
- NumPy

---

## Results

Stratified sampling shows:
- Lower variance (i.e., narrower confidence interval) compared to standard Monte Carlo

---
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
- Simulate terminal stock prices using GBM
- Compute discounted payoff
- Take average over all paths

### Stratified Sampling
- Construct strata based on the terminal value of the Wiener process
- Sample from each stratum
- Reduce variance compared to naive Monte Carlo

---

## Features

- GBM-based stock price simulation
- European call option pricing
- Standard Monte Carlo estimator
- Stratified sampling implementation
- Confidence interval comparison between methods

---

## Tech Stack

- Python
- NumPy

---

## Results

Stratified sampling shows:
- Lower variance (i.e., narrower confidence interval) compared to standard Monte Carlo

---
