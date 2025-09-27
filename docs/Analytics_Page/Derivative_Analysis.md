---
layout: default
title: Spectra Derivation
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Derivative_Analysis/
nav_order: 3
---

# Spectra Derivation
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

SpectraGuru offers a derivative analysis feature that plots the first and second derivative of your spectral data. This may be useful for analyzing and identifying abnormal trends in the data from a fresh perspective while also eliminating discrepancies caused by any constant shift in measured intensity between samples. On top of this, you may optionally normalize the derivative plots to further enhance the visualization.

## How to Use

0. In the analytics page, after processing your data, select “Spectra Derivation” from the drop-down menu on the left sidebar.
1. Select which normalization method you would like to use, if any. So far, only min/max normalization is offered for derivative analysis.
2. Finally, adjust the Savitzky-Golay parameters (window length and polynomial order) for the derivation process. This will be used to systematically derive your spectra by fitting them to polynomial curves (for more about Savitzky-Golay, see our documentation on [Smoothening](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Smoothening/)).
    - Window length (defaults to 11): Should be odd. Smaller values are typically better for noisy data, and larger values are typically better for data with sharp peaks.
    - Polynomial order (defaults to 3): Should be less than the window length. Higher values will fit the spectra more closely but will also retain noise.
3. On the right, two plots will be displayed: The top plot shows the first derivative $(\text{a.u.}/{\text{cm}^{-1}})$, and the bottom plot shows the second derivative $(\text{a.u.}/{\text{cm}^{-2}})$. Each sample (including the average spectrum) is plotted on the same graph.

## Behavior

- What is being plotted: The derivative plot of a spectrum attempts to encapsulate the rate of change in intensity observed at each Ramanshift with respect to wavenumber (how quickly intensity increases/decreases as wavenumber increases). The first derivative is the derivative of the original data, and the second derivative is the derivative of the first derivative.
- Algorithm: To differentiate your data, SpectraGuru uses a Savitzky-Golay filter, which first smooths out your data by fitting small windows of it to a polynomial curve. This polynomial is what is differentiated to approximate the true derivative of your data.
- Normalization: Currently, one optional normalization method is offered (min/max normalization), which rescales the derivative plots after computing them. The plots are rescaled so that the highest peak is at `1.0` and the lowest point is at `0.0` (for more about min/max normalization, see our [Normalization](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Normalization/) documentation).

## References

SpectraGuru uses SciPy's [`signal.savgol_filter`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html) function to differentiate your data.

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17(3), 261–272. https://doi.org/10.1038/s41592-019-0686-2