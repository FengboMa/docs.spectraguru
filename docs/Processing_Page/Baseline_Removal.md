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

## Behavior

This feature should identify and remove unwanted baselines from spectral data using one of three algorithms:
- AirPLS: Iteratively adjusts the baseline using a penalized least squares approach to smooth the background while preserving peaks. 
- ModPoly: Fits a polynomial function to estimate and subtract the baseline from the spectra.
- Gaussian-Lorentzian Fitting: Uses a Gaussian-Lorentzian hybrid to fit the data and find a baseline.
