---
layout: default
title: Interpolation
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Interpolation/
nav_order: 1
math: katex
---

# Interpolation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Interpolation resamples spectral intensities onto consecutive integer Raman shift values. The new axis runs from the first integer at or above the original minimum to the last integer at or below the original maximum. Each integer appears once, even when the original Raman shifts are unevenly spaced.

## How to use

To interpolate your data:

1. Upload data and open **Processing Page**.
2. Turn on **Interpolation** in the sidebar.
3. Click **Process** at the bottom of the sidebar.

## Behavior

After interpolation, Raman shifts are consecutive integers with no duplicates or gaps. Spectra share this new axis, and each intensity is calculated by linear interpolation between its neighboring original data points.

## Method

SpectraGuru constructs the integer grid from $\lceil x_{\min}\rceil$ through $\lfloor x_{\max}\rfloor$ in steps of one, then uses SciPy's [`interp1d`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.interpolate.interp1d.html#scipy.interpolate.interp1d) with linear interpolation to estimate each spectrum's intensity on that grid.

The interpolation can be represented mathematically as:

$$
I(x) = I(x_i) + \frac{I(x_{i+1}) - I(x_i)}{x_{i+1} - x_i} \times (x - x_i)
$$

where:
- $I(x)$ is the interpolated intensity at a new Ramanshift value $x$,
- $I(x_i)$ and $I(x_{i+1})$ are the intensities at the original Ramanshift values $x_i$ and $x_{i+1}$,
- $x$ is the new Ramanshift value to which interpolation is applied,
- $x_i$ and $x_{i+1}$ are the original Ramanshift values that bracket $x$.

This resamples the data onto a consistent axis without rounding individual original Raman shifts or intentionally smoothing their intensities.

## References

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. *Nature Methods*, 17, 261-272. https://doi.org/10.1038/s41592-019-0686-2
2. SciPy Developers. `scipy.interpolate.interp1d`. https://docs.scipy.org/doc/scipy/reference/generated/scipy.interpolate.interp1d.html
