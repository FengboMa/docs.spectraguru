---
layout: default
title: Gaussian Peak Fitting
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Gaussian_Peak_Fitting/
nav_order: 7
---

# Gaussian Peak Fitting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Gaussian Peak Fitting estimates Gaussian components for selected spectral peaks. It helps users inspect approximate peak centers, widths, amplitudes, and fitted peak shapes.

## How to use

1. Upload data and finish preprocessing if needed.
2. Open **Analytics Page**.
3. In **Select Analytics Plot**, choose **Gaussian Peak Fitting**.
4. Select or identify peaks using the available peak fitting controls.
5. Review the fitted curves and fitting parameters.

## Behavior

SpectraGuru fits Gaussian-shaped components to selected peak regions and displays the fitted result over the spectrum. The output helps compare measured peak structure with the fitted Gaussian approximation.

## Method

The fitted signal is a sum of Gaussian components:

$$\hat{I}(x)=\sum_{k=1}^{K} A_k\exp\left(-\frac{(x-\mu_k)^2}{2\sigma_k^2}\right)$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Selected peaks | Tunable | Peaks chosen through the peak fitting workflow |
| Component shape | Fixed | Gaussian components |
| Fitting routine | Fixed | SciPy nonlinear curve fitting |

## References

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. *Nature Methods*, 17, 261-272. https://doi.org/10.1038/s41592-019-0686-2
2. SciPy Developers. `scipy.optimize.curve_fit`. https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html
