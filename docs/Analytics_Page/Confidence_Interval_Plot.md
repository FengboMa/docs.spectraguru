---
layout: default
title: Confidence Interval Plot
parent: Analytics Features
grand_parent: Analytics Page
permalink: /docs/Analytics_Page/Analytics_Features/Confidence_Interval_Plot/
nav_order: 2
---

# Confidence Interval Plot
{: .no_toc }

## Table of Contents
{: .no_toc .text_delta}

1. TOC
{:toc}

---

## Introduction

The confidence interval plot is a concise way to view both the mean intensities and standard deviations all at once. This feature creates a plot of the average spectrum and includes a light blue region around the line representing a spread of one standard deviation from the mean. This is useful for visualizing which Raman shifts result in the most or least variation (potentially noise) between the selected spectra.

## How to use

0. In the analytics page, after processing your data, select “Confidence Interval Plot” from the drop-down menu on the left sidebar.
1. The bold blue line represents the average spectrum, and the light blue region represents values within one standard deviation from the mean.

## Behavior

The page shows the mean spectrum with an uncertainty band. In **Confidence Interval** mode, the band estimates uncertainty in the mean using the selected confidence level. In **Standard Deviation** mode, the band shows spread among individual spectra using the selected number of standard deviations.

## Method

Confidence interval mode uses:

$$CI(x)=\bar{I}(x)\pm t_{\alpha/2,n-1}\frac{s(x)}{\sqrt{n}}$$

Standard deviation mode uses:

$$B(x)=\bar{I}(x)\pm k\,s(x)$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| Interval Method | Tunable | `Confidence Interval` or `Standard Deviation` |
| Confidence Level | Tunable | `90`, `95`, or `99`; default `95` |
| Number of Standard Deviations | Tunable | `1`, `2`, or `3`; default `1` |
| Output | Fixed | Mean spectrum with an uncertainty band |

## References

1. Student. (1908). The probable error of a mean. *Biometrika*, 6(1), 1-25. https://doi.org/10.1093/biomet/6.1.1
2. SciPy Developers. Statistical functions. https://docs.scipy.org/doc/scipy/reference/stats.html
