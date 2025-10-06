---
layout: default
title: Savitzky-Golay Filter
parent: Smoothening
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Smoothening/Savitzky-Golay/
nav_order: 1
---

# Savitzky-Golay Filter
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How to Use

To apply Savitzky-Golay smoothening to your data:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Smoothening" toggle.
2. Select "Savitzky-Golay filter" from the drop-down menu.
3. Configure parameters:
    - Window length (defaults to `15`)
    - Polynomial order (defaults to `2`) - Should be less than window length.

## Behavior

If "Savitky-Golay filter" is selected, SpectraGuru's smoothening feature applies SciPy's implementation [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) to each spectrum, which works as follows:
0. For each Ramanshift value $x$, consider the values between $x-\frac{w}{2}$ and $x+\frac{w}{2}$, where $w$ is the window length.
1. Try to find the polynomial with order $d$ that best fits with the data centered around $x$. Mathematically speaking, this can be thought of as a minimization of the following expression as the coefficients $a_i$ vary:

    $$
    \sum_{j=-w/2}^{w/2} \left(I(x+j)-\sum_{i=0}^d \left(a_i (x+j)^i\right)\right)^2
    $$

    where $I(x)$ is the actual intensity at Ramanshift $x$.
2. Minimize the above expression using least squares optimization on the coefficients $a_i$. Then use the polynomial fit to find the filtered intensity at Ramanshift $x$.
3. Repeat this process for all $x$.

## References

SpectraGuru uses SciPy's [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) function for Savitzky-Golay smoothening.

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17(3), 261–272. https://doi.org/10.1038/s41592-019-0686-2

---

[Back to Smoothening](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Smoothening/)
