---
layout: default
title: iModPoly
parent: Baseline Removal
grand_parent: Processing Feature
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/iModPoly/
nav_order: 6
---

# iModPoly
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Improved modified polynomial fitting (iModPoly) estimates and subtracts fluorescence background from a Raman spectrum. It first reduces the influence of peaks, then iteratively fits a polynomial to estimate the background.

## How to use

1. Upload spectra and open **Processing Page**.
2. Turn on **Baseline removal** and choose **iModPoly**.
3. Set the polynomial degree, number of peak removal procedures, two scaling factors, and polynomial-fitting termination criterion.
4. Apply preprocessing and inspect the baseline-corrected spectra.

## Behavior

In each peak-removal pass, points above a polynomial fit by more than the selected noise-scaled threshold are excluded from the next pass. The remaining points are used for iterative polynomial baseline fitting. Setting the number of peak-removal procedures to `0` skips that first stage but still runs the iterative polynomial fit.

The final polynomial is evaluated at the original wavenumbers and subtracted from the original intensity values. Wavenumbers are preserved in the corrected spectrum.

## Method

For each peak-removal pass, SpectraGuru fits a polynomial $p(x)$ and computes the standard deviation $\sigma$ of its residuals. It retains points satisfying $I(x)-p(x)-a_1\sigma<0$. On those retained points, the modified fitting stage repeatedly replaces intensities above $p(x)+a_2\sigma$ with that limit and refits the polynomial. Iteration continues while the residual standard deviation falls below the selected cutoff fraction of the previous iteration's value. A final polynomial fitted to the retained baseline estimate is evaluated on the original axis, giving corrected intensity $I_{\mathrm{corrected}}(x)=I(x)-B(x)$.

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| iModPoly polynomial degree | Tunable | Default `5`, range `1`–`20` |
| Number of peak removal procedures | Tunable | Default `1`, range `0`–`7` |
| Scaling factor for peak removal ($a_1$) | Tunable | Default `1.0`, range `0.0`–`2.0` |
| Scaling factor for polyfit ($a_2$) | Tunable | Default `0.0`, range `0.0`–`2.0` |
| Termination criteria for polynomial fitting | Tunable | Default `0.95`, range `0.95`–`0.99` |
| Baseline action | Fixed | Estimate and subtract background separately for each spectrum |

## References

1. Zhao, J., Lui, H., McLean, D. I., & Zeng, H. (2007). Automated autofluorescence background subtraction algorithm for biomedical Raman spectroscopy. *Applied Spectroscopy*, 61(11), 1225–1232. https://doi.org/10.1366/000370207782597003
