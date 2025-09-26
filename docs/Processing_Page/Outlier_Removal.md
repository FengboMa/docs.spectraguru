---
layout: default
title: Outlier Removal
parent: Processing Feature
grand_parent: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Outlier_Removal/
nav_order: 7
---

# Outlier Removal
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

The Outlier Removal feature in SpectraGuru is designed to identify and eliminate spectra that deviate significantly from the rest of the samples. This process improves the quality of spectral analysis by ensuring that anomalies or extreme values do not distort the results. There are three thresholds used to identify outliers: single threshold, distance threshold, and correlation threshold.

## How to Use

To remove outlying samples from your data:

0. Upload data and select the spectra to be processed.
1. Navigate to the sidebar and turn on the "Outlier Removal" toggle.
2. Adjust threshold values for one or more of the following detection criteria:
    - Single threshold: The maximum number of standard deviations from the mean any data point in a particular spectrum can be before being considered an outlier.
    - Distance threshold: The maximum number of standard deviations a spectrum can be from the average spectrum.
    - Correlation threshold: The maximum number of standard deviations from the mean a spectrum's correlation to the average spectrum can be.
3. Click "Process" to update the display.

## Behavior

When spectra are flagged for being an outlier, the entire spectrum is removed, not individual observations. The "average spectrum" is a new spectrum calculated by taking the mean intensity across all samples at each Ramanshift (see documentation on [Average Plot](/docs/Analytics_Page/Analytics_Features/Average_Plot/)).

A spectrum is flagged as an outlier if it fails any of the following three tests:

0. Single threshold: If a spectrum contains data that differs from the average spectrum too greatly at *any* Ramanshift value, it is considered an outlier. How much it is allowed to differ depends on the threshold value set by the user, which defaults to `4`. This value represents the number of *standard deviations* from the average spectrum that are allowed.
1. Distance threshold: The *distance* between a spectrum $S$ and the average spectrum $S_{\text{avg}}$ is calculated as $\sqrt{\sum_x \left(S(x)-S_{\text{avg}}(x)\right)^2}$. Spectra that are more than $d$ standard deviations away from the average spectrum, where $d$ is the threshold set by the user (defaults to `6`), will be considered outliers.
2. Correlation threshold: The *correlation* between a spectrum and the average spectrum is determined by the Pearson Correlation Coefficient between them (see documentation on the [Correlation Heatmap](/docs/Analytics_Page/Analytics_Features/Correlation_Heatmap/) for more about this). Spectra whose correlations to the average spectrum fall short by more than $d$ standard deviations, where $d$ is the threshold set by the user (defaults to `4`), will be considered outliers.

## References

SpectraGuru uses NumPy's [`corrcoef`](https://numpy.org/doc/stable/reference/generated/numpy.corrcoef.html) function to determine the correlation between two spectra for the purposes of outlier removal.

1. Harris, C. R., Millman, K. J., van der Walt, S. J., Gommers, R., Virtanen, P., Cournapeau, D., Wieser, E., Taylor, J., Berg, S., Smith, N. J., & others. (2020). Array programming with NumPy. Nature, 585(7825), 357–362. https://doi.org/10.1038/s41586-020-2649-2
