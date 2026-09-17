# Heston Model Calibration Under Market Stress

An empirical investigation into how optimisation method affects Heston stochastic volatility model calibration across calm and sustained high-volatility market regimes. This repository contains the research and computational work of my MSc Quantitative Finance and Data Science dissertation at Birkbeck, University of London.

## 🔍 Overview

The Heston model provides a flexible framework for modelling stochastic volatility and is widely used in derivative pricing. However, calibration requires solving a nonlinear optimisation problem, and the resulting parameter estimates can depend substantially on the optimisation method and market conditions.

This dissertation investigates how three optimisation approaches perform when calibrating the Heston model to observed option-implied volatility surfaces:

* Levenberg–Marquardt (LM)
* Nelder–Mead (NM)
* Differential Evolution (DE)

The analysis compares calibration fit, computational cost, parameter behaviour, and short-horizon out-of-sample performance across calm and sustained high-volatility regimes.

## ⚙️ Methodology

The study includes:

* Heston stochastic volatility model implementation
* Semi-analytical European option pricing using characteristic-function Fourier inversion
* Numerical handling of the Heston characteristic function
* Calibration to observed implied volatility surfaces
* Nonlinear least-squares optimisation using Levenberg–Marquardt
* Derivative-free local optimisation using Nelder–Mead
* Population-based global optimisation using Differential Evolution
* Comparison of calibration error using implied-volatility RMSE
* Analysis of calibrated parameter stability across market regimes
* Calm vs sustained high-volatility regime comparison
* Short-horizon out-of-sample testing using fixed calibrated parameter sets
* Sensitivity analysis examining the effect of including volatility-surface wings

## 📊 Key Findings

The empirical results demonstrate that optimiser performance is strongly dependent on both the optimisation method and market regime.

* Differential Evolution generally produced the strongest in-sample calibration fit, particularly on the full volatility surface, at substantially greater computational cost.
* Levenberg–Marquardt was highly efficient and, when successful, could produce calibration errors comparable to Differential Evolution.
* However, unconstrained Levenberg–Marquardt exhibited pronounced failure behaviour on the full surface during calm periods, terminating rapidly with economically invalid parameter values despite satisfying numerical termination criteria.
* Nelder–Mead generally produced weaker fits than the other methods, while requiring more computational effort than Levenberg–Marquardt.
* Calibration errors increased during sustained high-volatility periods across the optimisation methods, indicating greater difficulty reproducing stressed volatility surfaces.
* Calibrated Heston parameters changed systematically between calm and stressed regimes, including lower mean-reversion speeds and higher variance levels during sustained high volatility.
* Short-horizon out-of-sample testing showed that calibrated parameter sets can lose fit when carried forward to subsequent volatility surfaces, highlighting the temporal sensitivity of Heston calibration.
* Results were sensitive to the inclusion of volatility-surface wings, demonstrating the importance of the calibration dataset and objective surface when assessing optimiser performance.

Overall, the findings suggest that optimiser selection cannot be assessed solely on in-sample calibration error. Computational cost, parameter validity, numerical termination behaviour, regime sensitivity, and performance outside the calibration date are also important considerations.

## 🧮 Heston Model

The Heston model specifies the asset price and instantaneous variance dynamics as stochastic processes:

$$
dS_t = \mu S_t\,dt + \sqrt{v_t}S_t\,dW_t^S
$$

$$
dv_t = \kappa(\theta-v_t)\,dt + \sigma\sqrt{v_t}\,dW_t^v
$$

with

$$
dW_t^S\,dW_t^v = \rho\,dt.
$$

The five calibrated parameters are:

* $\kappa$ — variance mean-reversion speed
* $\theta$ — long-run variance
* $\sigma$ — volatility of variance
* $\rho$ — correlation between asset and variance shocks
* $v_0$ — initial variance

## 🔬 Research Focus

The central research question is:

> **How does optimisation method affect the fit, computational cost, parameter stability, and short-horizon out-of-sample performance of Heston model calibration under calm vs sustained high-volatility market conditions?**

The investigation focuses on whether an optimisation method that performs well under conventional market conditions continues to behave reliably when the volatility surface changes substantially.

## 🛠️ Technologies

* Python
* NumPy
* Pandas
* SciPy
* Matplotlib
* LaTeX

## 🧠 Skills Demonstrated

* Stochastic volatility modelling
* Heston model implementation
* Derivative pricing
* Characteristic-function methods
* Numerical optimisation
* Global and local optimisation
* Implied-volatility calibration
* Financial time-series and volatility-surface analysis
* Out-of-sample model evaluation
* Parameter stability analysis
* Quantitative research methodology
* Numerical diagnostics and model-risk analysis
* Python-based quantitative research workflows
* Technical writing and empirical investigation
