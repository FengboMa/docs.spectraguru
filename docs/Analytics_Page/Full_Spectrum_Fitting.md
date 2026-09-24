---
layout: default
title: Full Spectrum Fitting
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Full_Spectrum_Fitting/
nav_order: 8
---

# Full Spectrum Fitting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Full Spectrum Fitting represents a spectrum as a sum of peak-shaped components. It can estimate component centers, amplitudes, and widths across the spectrum using Gaussian, Lorentzian, or Pseudovoigt curves. Baseline removal before fitting is recommended.

## How to use

1. Upload data, complete any preprocessing, and open **Analytics Page**.
2. Select **Full Spectrum Fitting** from **Select analytics plot**.
3. Choose **Discrete** to set the number of components, or **Prominence-Based** to select components by peak-prominence rank.
4. Choose the **Average**, **All**, or one individual spectrum, then choose a **Peak Shape**.
5. For **Discrete**, set the number of peaks, cofit range multiplier, and runtime control. For **Prominence-Based**, set the peak ranking threshold.
6. Click **Run Fit** and review the fitted spectrum, residual, component parameters, and component curves. When fitting **All**, select which result to view.

## Behavior

The Discrete algorithm repeatedly locates a prominent peak in the remaining residual and fits it with nearby components, up to the requested number of peaks. The Prominence-Based algorithm derives a prominence threshold from the ranked peaks in the initial spectrum and continues fitting peaks that meet that threshold in the residual. Its ranking value gives an approximate, not exact, component count.

For each fitted spectrum, SpectraGuru displays the original signal, individual components, their summed fit, and a residual plot. A component-parameter table lists fitted centers, amplitudes, full widths at half maximum (FWHM), and the Pseudovoigt mixing fraction when applicable. The residual plot reports root mean squared error (RMSE).

## Method

The fitted signal is the sum of component curves:

$$\hat{I}(x)=\sum_{k=1}^{K} A_k S(x;\mu_k,w_k,\eta_k)$$

Here $A_k$ is amplitude, $\mu_k$ is center, $w_k$ is FWHM, and $\eta_k$ is used only for Pseudovoigt components. A Gaussian component has shape $G(x)=\exp[-4\ln(2)((x-\mu)/w)^2]$; a Lorentzian component has shape $L(x)=1/[1+4((x-\mu)/w)^2]$. The Pseudovoigt shape is $(1-\eta)G(x)+\eta L(x)$, with $0\leq\eta\leq1$. Fitting uses local nonlinear least squares, and $\mathrm{RMSE}=\sqrt{\operatorname{mean}[(I-\hat{I})^2]}$.

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Algorithm version | Tunable | Discrete or Prominence-Based |
| Peak shape | Tunable | Gaussian, Lorentzian, or Pseudovoigt |
| Number of peaks | Tunable | Discrete only; default `20`, range `1`–`40` |
| Peak ranking threshold | Tunable | Prominence-Based only; default `15`, range `1`–`30` |
| Cofit range multiplier | Tunable | Discrete only; default `0.7`, range `0.4`–`1.0` |
| Runtime control | Tunable | Discrete only; Quick, Standard, Slow, or Thorough limits nearby components cofit together |
| Peak detection and fitting | Fixed | SciPy `find_peaks` and `curve_fit` |

## References

1. SciPy Developers. [`scipy.signal.find_peaks`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.find_peaks.html).
2. SciPy Developers. [`scipy.optimize.curve_fit`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html).
