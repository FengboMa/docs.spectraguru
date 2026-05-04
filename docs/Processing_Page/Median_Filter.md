---
layout: default
title: Median Filter
parent: Smoothening
grand_parent: Processing Feature
permalink: /docs/Processing_Page/Processing_Feature/Smoothening/Median_Filter/
nav_order: 3
---

# Median Filter
{: .no_toc }

## How to use

1. Upload data, then open **Processing Page**.
2. Enable **Smoothening**.
3. In **Select your smoothening function**, choose **Median filter**.
4. Set **Window size** and **Padding method**.
5. Apply the processing workflow to update the spectra.

## Behavior

The median filter replaces each intensity value with the median value inside a local window. It is useful for reducing narrow spikes or isolated outlier points while preserving sharper edges better than a mean filter. Large windows can flatten real spectral features, so the smallest effective odd window size is usually preferred.

## Method

For each point $i$, SpectraGuru computes the median inside a centered window:

$$\hat{y}_i = \operatorname{median}\{y_j: j \in W_i\}$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Window size | Tunable | Odd integer from `3` to `51`; default `3` |
| Padding method | Tunable | `mirror`, `edge`, or `zero`; `edge` maps to SciPy `nearest`, `zero` maps to SciPy `constant` |
| Filtering function | Fixed | `scipy.ndimage.median_filter` |

## References

1. Virtanen, P., Gommers, R., Oliphant, T. E., Haberland, M., Reddy, T., Cournapeau, D., ... SciPy 1.0 Contributors. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. *Nature Methods*, 17, 261-272. https://doi.org/10.1038/s41592-019-0686-2
2. SciPy Developers. `scipy.ndimage.median_filter`. https://docs.scipy.org/doc/scipy/reference/generated/scipy.ndimage.median_filter.html
