---
layout: default
title: Savitzky-Golay Filter
parent: Smoothing
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Smoothing/Savitzky-Golay/
nav_order: 1
---

# Savitzky-Golay Filter
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Savitzky-Golay Filter smooths spectra by fitting a local polynomial in a moving window and evaluating the fitted center point.

## How to use

To apply Savitzky-Golay smoothing to your data:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the **Smoothing** toggle.
2. In **Select smoothing function**, choose **Savitzky-Golay filter**.
3. Configure parameters:
    - Window length (defaults to `15`)
    - Polynomial order (defaults to `2`) - Should be less than window length.

## Behavior

If **Savitzky-Golay filter** is selected, SpectraGuru's smoothing feature applies SciPy's implementation [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) to each spectrum, which works as follows:
0. For each Ramanshift value $x$, consider the values between $x-\frac{w}{2}$ and $x+\frac{w}{2}$, where $w$ is the window length.
1. Try to find the polynomial with order $d$ that best fits with the data centered around $x$. Mathematically speaking, this can be thought of as a minimization of the following expression as the coefficients $a_i$ vary:

    $$
    \sum_{j=-w/2}^{w/2} \left(I(x+j)-\sum_{i=0}^d \left(a_i (x+j)^i\right)\right)^2
    $$

    where $I(x)$ is the actual intensity at Ramanshift $x$.
2. Minimize the above expression using least squares optimization on the coefficients $a_i$. Then use the polynomial fit to find the filtered intensity at Ramanshift $x$.
3. Repeat this process for all $x$.

## Method

The filter fits a local polynomial in each moving window and uses the fitted center value:

$$\hat{y}_i = \sum_{j=-m}^{m} c_j y_{i+j}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Savitzky-Golay window length | Tunable | Default `15`, UI range `1`-`100` |
| Savitzky-Golay polynomial order | Tunable | Default `2`, UI range `1`-`15`; must be less than window length |
| Filtering function | Fixed | `scipy.signal.savgol_filter` |

## References

SpectraGuru uses SciPy's [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) function for Savitzky-Golay smoothing.

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17(3), 261–272. https://doi.org/10.1038/s41592-019-0686-2

---

[Back to Smoothing](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Smoothing/)
