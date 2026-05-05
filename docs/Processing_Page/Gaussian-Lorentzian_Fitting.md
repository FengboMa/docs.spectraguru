---
layout: default
title: Gaussian-Lorentzian Fitting
parent: Baseline Removal
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/Gaussian-Lorentzian_Fitting/
nav_order: 3
---

# Gaussian-Lorentzian Fitting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Gaussian-Lorentzian Fitting estimates a baseline from user-selected fitting ranges using a mixed peak-shape model. It is useful when the baseline can be approximated from selected spectral regions.

## How to use

1. Upload data and open **Processing Page**.
2. Enable **Baseline Removal**.
3. In **Select your baseline removal function**, choose **Gaussian-Lorentzian Fitting**.
4. Set **Number of fitting ranges**.
5. Enter the **Start of range** and **End of range** values.
6. Click **Apply fitting ranges**, then process the data.

## Behavior

SpectraGuru validates and clips fitting ranges to the data bounds, warns about invalid or overlapping ranges, fits the selected ranges, and subtracts the estimated baseline from each selected spectrum.

## Method

The fitted baseline uses a mixed Gaussian-Lorentzian shape:

$$b(x)=G(x;A,\mu,\sigma)+L(x;S,\mu,\gamma)$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Number of fitting ranges | Tunable | Default `2`, UI range `2`-`10` |
| Start/end range bounds | Tunable | Clipped to dataset Raman shift bounds and checked for overlap |
| Curve fitting | Fixed | Nonlinear least-squares fitting with user ranges |
| Baseline action | Fixed | Fitted baseline is subtracted from each selected spectrum |

## References

1. Chen, H., et al. (2022). Rapid and quantitative detection of respiratory viruses using surface-enhanced Raman spectroscopy and machine learning. *Biosensors and Bioelectronics*, 202, 114721. https://doi.org/10.1016/j.bios.2022.114721
2. SciPy Developers. `scipy.optimize.curve_fit`. https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html
