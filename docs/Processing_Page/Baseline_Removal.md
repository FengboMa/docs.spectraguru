---
layout: default
title: Baseline Removal
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/
nav_order: 5
---

# Baseline Removal
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The Baseline Removal function in SpectraGuru is designed to eliminate background noise from spectral data, improving the accuracy of signal interpretation and making it easier to identify peaks and trends. A "baseline" refers to a low-frequency trend in your data that may distract from the more interesting and informative features of your data. Baselines may be affected by instrumental drift, temperature changes, or other environmental factors during measurement. SpectraGuru provides three separate methods for baseline removal, namely: Adaptive Iterative Reweighted Penalized Least Squares (AirPLS), Modified Polynomial Fitting (ModPoly), and Gaussian-Lorentzian Fitting.

## How to Use

To apply baseline removal to your spectral data:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Baseline Removal" toggle.
2. Select a baseline removal method from the drop-down menu:
    - AirPLS (Adaptive Iteratively Reweighted Penalized Least Squares)
    - ModPoly (Modified Polynomial Fitting)
    - Gaussian-Lorentzian Fitting
3. Configure parameters based on the selected method:
    - For AirPLS:
        - Set lambda (defaults to 100) - controls the smoothness of the estimated baseline.
        - Set p-order (defaults to 1) - defines the penalty order for iterative reweighting.
        - Set max iterations (defaults to 15) - determines the maximum number of fitting iterations.
        - Set tolerance (tau) (defaults to 0.0010) - sets the convergence criterion for stopping iterations.
    - For ModPoly:
        - Set polynomial degree (defaults to 5) - determines the degree of the polynomial fit used for baseline correction.
    - For Gaussian-Lorentzian Fitting:
        - Choose the number of fitting ranges to use.
        - Use the textboxes that appear to set the starts and ends of those ranges.
        - Click "Apply fitting ranges" to apply the values specified.

## Behavior

This feature should identify and remove unwanted baselines from spectral data using one of three algorithms:
- AirPLS: Iteratively adjusts the baseline using a penalized least squares approach to smooth the background while preserving peaks. 
- ModPoly: Fits a polynomial function to estimate and subtract the baseline from the spectra.
- Gaussian-Lorentzian Fitting: Uses a pseudo-Voigt Gaussian-Lorentzian hybrid to fit the data and find a baseline.

## Method

- If using AirPLS, 
- If using ModPoly, 
- If using Gaussian-Lorentzian Fitting, 