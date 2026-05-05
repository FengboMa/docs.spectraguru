---
layout: default
title: AirPLS
parent: Baseline Removal
grand_parent: Processing Feature
ancestor: Processing Page
permalink: /docs/Processing_Page/Processing_Feature/Baseline_Removal/AirPLS/
nav_order: 1
---

# Adaptive Iteratively Reweighted Penalized Least Squares (AirPLS)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introduction

Adaptive Iteratively Reweighted Penalized Least Squares (AirPLS) estimates a smooth baseline by iteratively reweighting peaks and background points. It is useful for removing broad background trends while preserving sharper spectral peaks.

## How to use

To use AirPLS for baseline removal:

0. Upload data and select the spectra you want to process.
1. Navigate to the sidebar and turn on the "Baseline Removal" toggle.
2. Select "AirPLS" from the drop-down menu.
3. Configure parameters:
    - Set lambda (defaults to `100`) - controls the smoothness of the estimated baseline.
    - Set p-order (defaults to `1`) - defines the penalty order for iterative reweighting.
    - Set max iterations (defaults to `15`) - determines the maximum number of fitting iterations.
    - Set tolerance (tau) (defaults to `0.0010`) - sets the convergence criterion for stopping iterations.

## Behavior

AirPLS iteratively adjusts the baseline using a penalized least squares approach to smooth the background while preserving peaks.

A background vector is repeatedly adjusted according to how well it fits with a *weighted* version of the data. The weights change each iteration, and peaks in the data are intentionally given low weights so that they are less likely to be interfered with after baseline removal. AirPLS keeps refining the background vector until it is within the tolerance (tau) of the weighted data or it has reached the maximum number of iterations.

## Method

AirPLS estimates a smooth baseline by solving a penalized weighted least-squares problem:

$$\min_z \sum_i w_i(y_i-z_i)^2 + \lambda \lVert D z\rVert^2$$

| Parameter | Tunable or fixed | Implementation |
| --- | --- | --- |
| AirPLS lambda | Tunable | Default `100`, UI range `1`-`1000000` |
| AirPLS p-order | Tunable | Default `1`, UI range `1`-`10` |
| AirPLS maximum iterations | Tunable | Default `15`, UI range `5`-`1000` |
| AirPLS tolerance | Tunable | Default `0.001` |
| Baseline action | Fixed | Estimated baseline is subtracted from each selected spectrum |

## References

The AirPLS algorithm that SpectraGuru uses is a translation of the R source code from AirPLS version 2.0 by Yizeng Liang and Zhang Zhimin, which can be found at <https://code.google.com/p/airpls>.

1. Z.-M. Zhang, S. Chen, and Y.-Z. Liang, Baseline correction using adaptive iteratively reweighted penalized least squares. Analyst 135 (5), 1138-1146 (2010).

---

[Back to Baseline Removal](/docs.spectraguru/docs/Processing_Page/Processing_Feature/Baseline_Removal/)
